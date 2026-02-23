---
title: "Продвинутая настройка"
weight: 4
bookToc: true
---

# Продвинутая настройка

## Введение

В этом уроке мы рассмотрим продвинутые возможности настройки Pi Mono: кастомные модели, OAuth-провайдеры, контекстное управление и агентный цикл.

## Кастомные модели

Подключите любой OpenAI-совместимый API:

```typescript
import { getModel } from '@mariozechner/pi-ai';

const model = getModel('openai-compatible', 'my-model', {
  baseUrl: 'http://localhost:11434/v1',
  apiKey: 'ollama',
});
```

## OAuth-провайдеры

Для некоторых провайдеров (Vertex AI, GitHub Copilot, Codex) нужна OAuth-авторизация:

```bash
pi
/login  # Выберите провайдера и следуйте инструкциям
```

## Контекстное управление в Agent

### transformContext

Преобразует сообщения перед отправкой LLM:

```typescript
const agent = new Agent({
  initialState: { ... },
  transformContext: (messages) => {
    // Оставить только последние 20 сообщений
    return messages.slice(-20);
  },
});
```

### convertToLlm

Конвертирует пользовательские типы сообщений в формат LLM:

```typescript
convertToLlm: (messages) => {
  return messages.filter(m => m.type !== 'ui-only');
},
```

## Уровни «размышления» (Thinking)

```typescript
const model = getModel('anthropic', 'claude-sonnet-4-20250514');
// В stream/complete можно передать thinkingLevel
```

## Cross-Provider Handoffs

Передача контекста между разными LLM-провайдерами в рамках одной сессии.

## Итоги

- Кастомные модели через OpenAI-совместимый API
- OAuth для корпоративных провайдеров
- Гибкое управление контекстом через transform и convert
