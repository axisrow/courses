---
title: "Tools"
weight: 4
bookToc: true
---

# Tools

## Introduction

Tools are functions that an LLM can call to perform actions. Pi Mono provides a system for defining and handling tools.

## Built-in Pi Tools

The coding agent includes 4 basic tools:

- **read** — read files
- **write** — create/write files
- **edit** — edit existing files
- **bash** — execute shell commands

## Creating a Tool in pi-ai

```typescript
import { Type, Tool } from '@mariozechner/pi-ai';

const calculatorTool: Tool = {
  name: 'calculator',
  description: 'Performs mathematical calculations',
  parameters: Type.Object({
    expression: Type.String({ description: 'Math expression' }),
  }),
};
```

## Handling Tool Calls

```typescript
for await (const event of stream(model, ctx, { tools: [calculatorTool] })) {
  if (event.type === 'tool_call') {
    const result = eval(event.args.expression);
    ctx.addToolResult(event.id, String(result));
  }
}
```

## Tools in pi-agent-core

```typescript
const agent = new Agent({
  initialState: {
    systemPrompt: 'You are an assistant with a calculator.',
    model: getModel('anthropic', 'claude-sonnet-4-20250514'),
    tools: [calculatorTool],
  },
});
```

## Pi Extensions

Extensions are TypeScript modules that add new tools to the coding agent:

```typescript
// .pi/extensions/my-tool.ts
export default {
  name: 'my_tool',
  description: 'My tool',
  parameters: Type.Object({ input: Type.String() }),
  execute: async (args) => {
    return `Result: ${args.input}`;
  },
};
```

## Summary

- Tools let LLMs perform real actions
- pi-ai provides a typed tool definition system
- Coding agent is extensible via Extensions
