---
title: "LLM API (pi-ai)"
weight: 1
bookToc: true
---

# LLM API (pi-ai)

## Введение

Пакет `@mariozechner/pi-ai` предоставляет единый API для работы с множеством LLM-провайдеров. Вместо изучения API каждого провайдера, вы используете один интерфейс.

## Поддерживаемые провайдеры

- OpenAI, Azure OpenAI
- Anthropic
- Google, Vertex AI
- Mistral, Groq, Cerebras, xAI
- OpenRouter, Amazon Bedrock
- Любой OpenAI-совместимый API (Ollama, vLLM, LM Studio)

## Установка

```bash
npm install @mariozechner/pi-ai
```

## Быстрый старт

```typescript
import { getModel, stream, Context, Tool } from '@mariozechner/pi-ai';

// Получить модель
const model = getModel('anthropic', 'claude-sonnet-4-20250514');

// Создать контекст
const ctx = new Context();
ctx.addSystem('Ты полезный помощник.');
ctx.addUser('Привет!');

// Стриминг ответа
for await (const event of stream(model, ctx)) {
  if (event.type === 'text') {
    process.stdout.write(event.text);
  }
}
```

## Инструменты (Tools)

```typescript
import { Type } from '@mariozechner/pi-ai';

const weatherTool: Tool = {
  name: 'get_weather',
  description: 'Получить погоду в городе',
  parameters: Type.Object({
    city: Type.String({ description: 'Название города' }),
  }),
};
```

## Итоги

- pi-ai — единый API для 15+ LLM-провайдеров
- Поддерживает стриминг, инструменты, отслеживание токенов
- Работает в Node.js и в браузере
