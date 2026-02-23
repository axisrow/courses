---
title: "Интеграция с провайдерами"
level: 2
lesson: 5
lang: ru
tags: [провайдеры, модели, роли, мультикредentials]
---

# Интеграция с провайдерами

## Введение

OMP поддерживает десятки AI-провайдеров и позволяет гибко управлять моделями.

## Роли моделей

```
/model
```

| Роль | Назначение |
|------|-----------|
| default | Обычная работа |
| smol | Быстрые/дешёвые задачи |
| slow | Глубокий анализ |
| plan | Планирование (/plan) |
| commit | Коммиты и changelog |

CLI-переключение:

```bash
omp --model anthropic/claude-sonnet-4
omp --smol anthropic/claude-haiku
omp --slow anthropic/claude-opus
```

Горячие клавиши: `Ctrl+P` — цикл моделей, `Ctrl+L` — выбор.

## Мульти-credential поддержка

- Round-robin между API-ключами
- Автоматический fallback при rate limit
- Consistent hashing для стабильного распределения

## Поддерживаемые API

- `openai-completions`
- `openai-responses`
- `anthropic-messages`
- `google-generative-ai`
- `google-vertex`
- `azure-openai-responses`
- `openai-codex-responses`

## Cursor Provider

Используйте подписку Cursor Pro:

```
/login
# Выбрать Cursor
```

## Ollama (локальные модели)

```yaml
# ~/.omp/agent/models.yml
providers:
  ollama:
    baseUrl: http://localhost:11434/v1
    api: openai-completions
    models:
      - id: llama-3.1-8b
        name: Llama 3.1 8B
        contextWindow: 128000
```

## MCP и плагины

```bash
omp plugin install <name>
omp plugin enable <name>
omp plugin doctor
```

## Итоги

OMP поддерживает множество провайдеров с гибкой настройкой ролей, мульти-credential и MCP-интеграцией.
