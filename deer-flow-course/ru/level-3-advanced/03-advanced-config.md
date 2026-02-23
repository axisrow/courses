---
title: "Продвинутая конфигурация"
weight: 3
bookToc: true
---

# Продвинутая конфигурация

## Введение

В этом уроке мы разберём все возможности настройки DeerFlow для продвинутых сценариев использования.

## Полная структура config.yaml

```yaml
# Модели ИИ
models:
  - name: gpt-4o
    display_name: GPT-4o
    use: langchain_openai:ChatOpenAI
    model: gpt-4o
    api_key: $OPENAI_API_KEY
    max_tokens: 4096
    temperature: 0.7
    supports_vision: true
    supports_thinking: false

# Инструменты
tools:
  - name: web_search
    group: web
    use: src.community.tavily.tools:web_search_tool
  - name: web_fetch
    group: web
    use: src.community.jina_ai.tools:web_fetch_tool

# Группы инструментов
tool_groups:
  - name: web
  - name: file:read
  - name: file:write
  - name: bash

# Песочница
sandbox:
  use: src.sandbox.local:LocalSandboxProvider

# Навыки
skills:
  path: ../skills
  container_path: /mnt/skills

# Суб-агенты
subagents:
  enabled: true

# Память
memory:
  enabled: true
  injection_enabled: true
  storage_path: .deer-flow/memory.json
  debounce_seconds: 30
  model_name: null          # null = используется основная модель
  max_facts: 100
  fact_confidence_threshold: 0.7
  max_injection_tokens: 2000

# Генерация заголовков
title:
  enabled: true
  max_words: 10
  max_chars: 50

# Суммаризация
summarization:
  enabled: true
  trigger:
    type: tokens
    threshold: 100000
  keep:
    recent_messages: 10
```

## Переменные окружения

Значения, начинающиеся с `$`, подставляются из переменных окружения:

```yaml
api_key: $OPENAI_API_KEY  # Берётся из переменной OPENAI_API_KEY
```

Приоритет конфигурации:
1. Явный `config_path` в аргументах
2. Переменная `DEER_FLOW_CONFIG_PATH`
3. `config.yaml` в текущей директории
4. `config.yaml` в родительской директории (рекомендуется)

## Настройка моделей

### Модели с поддержкой Thinking

```yaml
models:
  - name: deepseek-v3
    use: langchain_deepseek:ChatDeepSeek
    model: deepseek-chat
    api_key: $DEEPSEEK_API_KEY
    supports_thinking: true
    when_thinking_enabled:
      extra_body:
        thinking:
          type: enabled
```

### Модели с Vision

```yaml
models:
  - name: gpt-4o
    use: langchain_openai:ChatOpenAI
    model: gpt-4o
    api_key: $OPENAI_API_KEY
    supports_vision: true   # Включает view_image инструмент
```

### Локальные модели

```yaml
models:
  - name: ollama-llama
    display_name: Llama 3 (Local)
    use: langchain_openai:ChatOpenAI
    model: llama3
    base_url: http://localhost:11434/v1
    api_key: ollama          # Ollama не требует ключ
```

## Настройка суммаризации

### По количеству токенов

```yaml
summarization:
  enabled: true
  trigger:
    type: tokens
    threshold: 100000       # Сжимать после 100K токенов
```

### По количеству сообщений

```yaml
summarization:
  enabled: true
  trigger:
    type: messages
    threshold: 50           # Сжимать после 50 сообщений
```

### По доле контекстного окна

```yaml
summarization:
  enabled: true
  trigger:
    type: fraction
    threshold: 0.75         # Сжимать при 75% заполнения
```

## Настройка MCP-серверов

### extensions_config.json

```json
{
  "mcpServers": {
    "filesystem": {
      "enabled": true,
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/tmp"],
      "description": "Доступ к файловой системе"
    },
    "remote-api": {
      "enabled": true,
      "type": "sse",
      "url": "http://my-server:3000/sse",
      "headers": {
        "Authorization": "Bearer token123"
      }
    }
  },
  "skills": {
    "research": { "enabled": true },
    "report-generation": { "enabled": true },
    "custom-skill": { "enabled": true }
  }
}
```

### Обновление MCP в runtime

MCP-конфигурацию можно менять на лету через API:

```bash
curl -X PUT http://localhost:2026/api/mcp/config \
  -H "Content-Type: application/json" \
  -d '{"mcpServers": {"new-tool": {"enabled": true, "type": "stdio", "command": "my-tool"}}}'
```

LangGraph обнаружит изменения через mtime файла и перезагрузит инструменты.

## Runtime-конфигурация

Некоторые параметры можно менять для каждого запроса:

```json
{
  "configurable": {
    "thinking_enabled": true,    // Включить reasoning
    "model_name": "gpt-4o",     // Выбрать модель
    "is_plan_mode": true,        // Режим плана
    "subagent_enabled": true     // Суб-агенты
  }
}
```

## Итоги

- `config.yaml` — центральный файл конфигурации
- Поддерживаются переменные окружения через префикс `$`
- Модели настраиваются с поддержкой thinking, vision
- Суммаризация настраивается по токенам, сообщениям или доле
- MCP-серверы обновляются в runtime через API
- Runtime-параметры позволяют менять поведение на лету
