---
title: "Архитектура DeerFlow"
weight: 1
bookToc: true
---

# Архитектура DeerFlow

## Введение

В этом уроке мы «заглянем под капот» DeerFlow и разберём, как устроена система изнутри. Понимание архитектуры поможет вам эффективнее настраивать, расширять и отлаживать DeerFlow.

## Общая архитектура

```
                    ┌──────────────────────────────────────┐
                    │          Nginx (порт 2026)            │
                    │      Единый обратный прокси           │
                    └───────┬──────────────────┬───────────┘
                            │                  │
          /api/langgraph/*  │                  │  /api/* (остальное)
                            ▼                  ▼
           ┌────────────────────┐  ┌────────────────────────┐
           │ LangGraph Server   │  │   Gateway API (8001)   │
           │    (порт 2024)     │  │   FastAPI REST         │
           └────────────────────┘  └────────────────────────┘
                    │
           ┌────────────────┐
           │  Lead Agent     │
           │  ├─ Middleware  │
           │  ├─ Tools       │
           │  └─ Subagents   │
           └────────────────┘
```

### Компоненты

| Компонент | Порт | Технология | Назначение |
|-----------|------|------------|------------|
| **Nginx** | 2026 | Nginx | Обратный прокси, единая точка входа |
| **Frontend** | 3000 | Next.js | Веб-интерфейс пользователя |
| **Gateway API** | 8001 | FastAPI | REST API для моделей, MCP, навыков, памяти |
| **LangGraph Server** | 2024 | LangGraph | Среда выполнения агентов |

### Маршрутизация запросов

Nginx распределяет запросы:
- `/api/langgraph/*` → LangGraph Server (взаимодействие с агентом)
- `/api/*` → Gateway API (управление конфигурацией)
- `/` → Frontend (веб-интерфейс)

## Lead Agent

Главный агент создаётся функцией `make_lead_agent(config)` и включает:

1. **Динамический выбор модели** через `create_chat_model()`
2. **Цепочку middleware** для обработки запросов
3. **Систему инструментов** через `get_available_tools()`
4. **Системный промпт** с навыками, памятью и инструкциями

## Цепочка Middleware

Middleware — это компоненты, которые обрабатывают запрос последовательно, как фильтры. Каждый отвечает за свою задачу:

| # | Middleware | Назначение |
|---|-----------|------------|
| 1 | **ThreadDataMiddleware** | Создаёт директории для каждого потока |
| 2 | **UploadsMiddleware** | Инжектирует загруженные файлы в контекст |
| 3 | **SandboxMiddleware** | Получает песочницу для выполнения кода |
| 4 | **DanglingToolCallMiddleware** | Обрабатывает незавершённые вызовы инструментов |
| 5 | **SummarizationMiddleware** | Сжимает контекст при приближении к лимиту |
| 6 | **TodoListMiddleware** | Отслеживает задачи в режиме плана |
| 7 | **TitleMiddleware** | Генерирует заголовок разговора |
| 8 | **MemoryMiddleware** | Отправляет разговоры на анализ памяти |
| 9 | **ViewImageMiddleware** | Инжектирует изображения для моделей с vision |
| 10 | **SubagentLimitMiddleware** | Ограничивает число суб-агентов |
| 11 | **ClarificationMiddleware** | Перехватывает запросы уточнений (всегда последний) |

### Порядок важен!

ClarificationMiddleware **обязательно** должен быть последним, так как он прерывает выполнение через `Command(goto=END)`.

## Система инструментов

```python
get_available_tools(groups, include_mcp, model_name, subagent_enabled)
```

Собирает инструменты из нескольких источников:

1. **Config-defined** — из `config.yaml` через `resolve_variable()`
2. **MCP** — из включённых MCP-серверов (ленивая инициализация, кеш)
3. **Built-in** — `present_files`, `ask_clarification`, `view_image`
4. **Subagent** — инструмент `task` для делегирования

## Система рефлексии (Reflection)

DeerFlow использует **динамическую загрузку модулей**:

```python
# Загрузка переменной из модуля
resolve_variable("src.community.tavily.tools:web_search_tool")

# Загрузка класса с проверкой типа
resolve_class("src.sandbox.local:LocalSandboxProvider", SandboxProvider)
```

Это позволяет настраивать компоненты через строки в `config.yaml` без изменения кода.

## Структура проекта

```
deer-flow/
├── backend/
│   ├── src/
│   │   ├── agents/           # Система агентов
│   │   │   ├── lead_agent/   # Главный агент
│   │   │   ├── middlewares/   # 11 middleware-компонентов
│   │   │   ├── memory/        # Система памяти
│   │   │   └── thread_state.py
│   │   ├── gateway/           # REST API
│   │   ├── sandbox/           # Система песочниц
│   │   ├── subagents/         # Система суб-агентов
│   │   ├── tools/             # Встроенные инструменты
│   │   ├── mcp/               # MCP-интеграция
│   │   ├── models/            # Фабрика моделей
│   │   ├── skills/            # Система навыков
│   │   ├── config/            # Система конфигурации
│   │   └── community/         # Community-инструменты
│   └── tests/
├── frontend/                   # Next.js
├── skills/                     # Навыки
└── config.yaml                 # Конфигурация
```

## ThreadState

Состояние каждого потока (разговора):

```python
class ThreadState:
    messages: list          # История сообщений
    sandbox: str            # ID песочницы
    thread_data: dict       # Данные потока
    title: str              # Заголовок
    artifacts: list         # Артефакты (файлы)
    todos: list             # Список задач
    uploaded_files: list    # Загруженные файлы
    viewed_images: list     # Просмотренные изображения
```

## Итоги

- DeerFlow построен на 4 сервисах: Nginx, Frontend, Gateway API, LangGraph
- Главный агент использует цепочку из 11 middleware
- Инструменты собираются из конфигурации, MCP, built-in и суб-агентов
- Динамическая загрузка модулей через систему рефлексии
- Каждый разговор имеет изолированное состояние (ThreadState)
