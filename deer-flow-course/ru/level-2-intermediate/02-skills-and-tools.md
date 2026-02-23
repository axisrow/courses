---
title: "Skills & Tools"
weight: 2
bookToc: true
---

# Skills & Tools (Навыки и инструменты)

## Введение

**Skills** (навыки) и **Tools** (инструменты) — это то, что делает DeerFlow по-настоящему универсальным. Навыки определяют *что* агент умеет делать, а инструменты — *как* он это делает.

## Навыки (Skills)

### Что такое навык?

**Навык** — это файл с инструкциями (Markdown), который описывает пошаговый процесс выполнения определённого типа задач. Это как подробная должностная инструкция для ИИ-агента.

### Встроенные навыки

DeerFlow поставляется с набором готовых навыков:

| Навык | Описание |
|-------|----------|
| `research` | Глубокое исследование тем с поиском источников |
| `report-generation` | Создание структурированных отчётов |
| `slide-creation` | Генерация презентаций |
| `web-page` | Создание HTML/CSS веб-страниц |
| `image-generation` | Генерация изображений |

### Где хранятся навыки

```
deer-flow/skills/
├── public/                    ← встроенные навыки
│   ├── research/SKILL.md
│   ├── report-generation/SKILL.md
│   ├── slide-creation/SKILL.md
│   ├── web-page/SKILL.md
│   └── image-generation/SKILL.md
└── custom/                    ← ваши навыки (добавьте сюда)
    └── your-skill/SKILL.md
```

### Структура файла SKILL.md

Каждый навык — это Markdown-файл с YAML-метаданными:

```markdown
---
name: my-skill
description: "Описание навыка"
license: MIT
allowed-tools:
  - web_search
  - write_file
  - bash
---

# Инструкции для агента

Пошаговый процесс...
```

- **name** — уникальное имя навыка
- **description** — описание для агента
- **allowed-tools** — какие инструменты навык может использовать
- Тело файла — инструкции, которые агент будет следовать

### Прогрессивная загрузка

Навыки загружаются **только по необходимости**. Если вы попросите создать отчёт — загрузится навык `report-generation`. Если попросите исследовать тему — загрузится `research`. Это экономит контекстное окно (количество текста, которое ИИ может обработать за раз).

## Инструменты (Tools)

### Типы инструментов

1. **Встроенные** — поставляются с DeerFlow (bash, ls, read_file, write_file и др.)
2. **Community** — от сообщества (tavily, jina_ai, firecrawl, image_search)
3. **MCP** — подключаемые через стандарт MCP
4. **Кастомные** — ваши собственные Python-функции

### Настройка инструментов в config.yaml

```yaml
tools:
  - name: web_search
    group: web
    use: src.community.tavily.tools:web_search_tool
    max_results: 5

  - name: web_fetch
    group: web
    use: src.community.jina_ai.tools:web_fetch_tool
```

### Группы инструментов

Инструменты организованы в **группы** — логические категории:

```yaml
tool_groups:
  - name: web         # Поиск и загрузка веб-страниц
  - name: file:read   # Чтение файлов
  - name: file:write  # Запись файлов
  - name: bash        # Выполнение команд
```

## MCP-серверы

**MCP** (Model Context Protocol) — это стандартный протокол для подключения внешних инструментов. Настройка в `extensions_config.json`:

```json
{
  "mcpServers": {
    "github": {
      "enabled": true,
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "your-token"
      },
      "description": "Работа с GitHub"
    }
  }
}
```

### Типы подключения MCP

| Тип | Описание | Пример |
|-----|----------|--------|
| `stdio` | Запускает программу | `npx my-server` |
| `sse` | Подключается по URL (SSE) | `http://host:port/sse` |
| `http` | Подключается по URL (HTTP) | `http://host:port` |

## Управление навыками через API

DeerFlow предоставляет REST API для управления навыками:

- `GET /api/skills` — список всех навыков
- `GET /api/skills/{name}` — детали навыка
- `PUT /api/skills/{name}` — включить/выключить навык
- `POST /api/skills/install` — установить новый навык из .skill-архива

## Итоги

- Навыки — это Markdown-инструкции, расширяющие возможности агента
- Инструменты — это функции, которые агент вызывает для действий
- Навыки загружаются прогрессивно для экономии контекста
- MCP позволяет подключать внешние инструменты
- Можно создавать свои навыки и инструменты
