---
title: "高级配置"
weight: 4
bookToc: true
---

# 高级配置

## 简介

本课涵盖 Pi Mono 的高级配置：自定义模型、OAuth 提供商、上下文管理和代理循环。

## 自定义模型

连接任何 OpenAI 兼容 API：

```typescript
import { getModel } from '@mariozechner/pi-ai';

const model = getModel('openai-compatible', 'my-model', {
  baseUrl: 'http://localhost:11434/v1',
  apiKey: 'ollama',
});
```

## OAuth 提供商

某些提供商（Vertex AI、GitHub Copilot、Codex）需要 OAuth：

```bash
pi
/login  # 选择提供商并按照说明操作
```

## Agent 中的上下文管理

### transformContext

在发送给 LLM 之前转换消息：

```typescript
const agent = new Agent({
  initialState: { ... },
  transformContext: (messages) => {
    return messages.slice(-20);
  },
});
```

### convertToLlm

将自定义消息类型转换为 LLM 格式：

```typescript
convertToLlm: (messages) => {
  return messages.filter(m => m.type !== 'ui-only');
},
```

## 思考级别

```typescript
const model = getModel('anthropic', 'claude-sonnet-4-20250514');
// 在 stream/complete 选项中传递 thinkingLevel
```

## 跨提供商切换

在单个会话中在不同 LLM 提供商之间传递上下文。

## 总结

- 通过 OpenAI 兼容 API 使用自定义模型
- 企业提供商的 OAuth
- 通过 transform 和 convert 灵活管理上下文
