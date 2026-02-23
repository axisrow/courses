---
title: "Интеграция навыков с MCP"
weight: 3
bookToc: true
---

# Интеграция навыков с MCP

## Введение

MCP (Model Context Protocol) — протокол для подключения LLM к внешним сервисам. Навык `mcp-builder` помогает создавать MCP-серверы.

## Что такое MCP

MCP позволяет Claude:
- Подключаться к базам данных
- Вызывать внешние API
- Работать с файловыми системами
- Управлять сервисами

## Навык mcp-builder

Структура:

```
mcp-builder/
├── SKILL.md
└── reference/
    ├── evaluation.md           # Критерии оценки
    ├── python_mcp_server.md    # Python FastMCP
    └── mcp_best_practices.md   # Лучшие практики
```

### Что умеет

- Создание MCP-серверов на Python (FastMCP) и TypeScript (MCP SDK)
- Проектирование инструментов для LLM
- Оценка качества MCP-серверов

## Связь Skills + MCP

Skills и MCP дополняют друг друга:

| Skills | MCP |
|--------|-----|
| Инструкции и процессы | Подключение к сервисам |
| Текстовые правила | Программные интерфейсы |
| Статические знания | Динамические данные |

### Пример комбинации

Навык может инструктировать Claude использовать MCP-инструмент:

```markdown
---
name: database-reporter
description: Creates database reports using MCP database tools
---

# Database Reporter

## Process
1. Connect to database using MCP tool `query_db`
2. Execute the analysis query
3. Format results as a markdown table
4. Generate summary with insights
```

## Создание MCP-сервера с помощью навыка

```
Пользователь: Создай MCP-сервер для работы с GitHub Issues

Claude (с навыком mcp-builder): 
1. Проектирует инструменты (list_issues, create_issue, update_issue)
2. Генерирует код на Python с FastMCP
3. Добавляет обработку ошибок и валидацию
4. Создаёт тесты
```

## Итоги

- MCP — протокол подключения LLM к внешним сервисам
- Навык `mcp-builder` помогает создавать MCP-серверы
- Skills и MCP дополняют друг друга
- Навыки могут инструктировать Claude использовать MCP-инструменты
