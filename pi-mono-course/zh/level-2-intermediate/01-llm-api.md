---
title: "LLM API (pi-ai)"
weight: 1
bookToc: true
---

# LLM API (pi-ai)

## 简介

`@mariozechner/pi-ai` 包提供了统一的 API，用于与多个 LLM 提供商交互。无需学习每个提供商的 API，只需使用一个接口。

## 支持的提供商

- OpenAI、Azure OpenAI
- Anthropic
- Google、Vertex AI
- Mistral、Groq、Cerebras、xAI
- OpenRouter、Amazon Bedrock
- 任何 OpenAI 兼容 API（Ollama、vLLM、LM Studio）

## 安装

```bash
npm install @mariozechner/pi-ai
```

## 快速开始

```typescript
import { getModel, stream, Context, Tool } from '@mariozechner/pi-ai';

const model = getModel('anthropic', 'claude-sonnet-4-20250514');

const ctx = new Context();
ctx.addSystem('你是一个有用的助手。');
ctx.addUser('你好！');

for await (const event of stream(model, ctx)) {
  if (event.type === 'text') {
    process.stdout.write(event.text);
  }
}
```

## 工具（Tools）

```typescript
import { Type } from '@mariozechner/pi-ai';

const weatherTool: Tool = {
  name: 'get_weather',
  description: '获取城市天气',
  parameters: Type.Object({
    city: Type.String({ description: '城市名称' }),
  }),
};
```

## 总结

- pi-ai 是 15+ LLM 提供商的统一 API
- 支持流式传输、工具、令牌跟踪
- 在 Node.js 和浏览器中均可使用
