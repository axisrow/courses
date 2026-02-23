---
title: "LLM API (pi-ai)"
weight: 1
bookToc: true
---

# LLM API (pi-ai)

## Introduction

The `@mariozechner/pi-ai` package provides a unified API for working with many LLM providers. Instead of learning each provider's API, you use one interface.

## Supported Providers

- OpenAI, Azure OpenAI
- Anthropic
- Google, Vertex AI
- Mistral, Groq, Cerebras, xAI
- OpenRouter, Amazon Bedrock
- Any OpenAI-compatible API (Ollama, vLLM, LM Studio)

## Installation

```bash
npm install @mariozechner/pi-ai
```

## Quick Start

```typescript
import { getModel, stream, Context, Tool } from '@mariozechner/pi-ai';

const model = getModel('anthropic', 'claude-sonnet-4-20250514');

const ctx = new Context();
ctx.addSystem('You are a helpful assistant.');
ctx.addUser('Hello!');

for await (const event of stream(model, ctx)) {
  if (event.type === 'text') {
    process.stdout.write(event.text);
  }
}
```

## Tools

```typescript
import { Type } from '@mariozechner/pi-ai';

const weatherTool: Tool = {
  name: 'get_weather',
  description: 'Get weather for a city',
  parameters: Type.Object({
    city: Type.String({ description: 'City name' }),
  }),
};
```

## Summary

- pi-ai is a unified API for 15+ LLM providers
- Supports streaming, tools, token tracking
- Works in Node.js and browsers
