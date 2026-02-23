---
title: "Advanced Configuration"
weight: 4
bookToc: true
---

# Advanced Configuration

## Introduction

This lesson covers advanced Pi Mono configuration: custom models, OAuth providers, context management, and the agent loop.

## Custom Models

Connect any OpenAI-compatible API:

```typescript
import { getModel } from '@mariozechner/pi-ai';

const model = getModel('openai-compatible', 'my-model', {
  baseUrl: 'http://localhost:11434/v1',
  apiKey: 'ollama',
});
```

## OAuth Providers

Some providers (Vertex AI, GitHub Copilot, Codex) require OAuth:

```bash
pi
/login  # Select provider and follow instructions
```

## Context Management in Agent

### transformContext

Transforms messages before sending to LLM:

```typescript
const agent = new Agent({
  initialState: { ... },
  transformContext: (messages) => {
    return messages.slice(-20);
  },
});
```

### convertToLlm

Converts custom message types to LLM format:

```typescript
convertToLlm: (messages) => {
  return messages.filter(m => m.type !== 'ui-only');
},
```

## Thinking Levels

```typescript
const model = getModel('anthropic', 'claude-sonnet-4-20250514');
// Pass thinkingLevel in stream/complete options
```

## Cross-Provider Handoffs

Transfer context between different LLM providers within a single session.

## Summary

- Custom models via OpenAI-compatible API
- OAuth for enterprise providers
- Flexible context management via transform and convert
