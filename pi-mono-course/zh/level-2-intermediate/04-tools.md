---
title: "工具（Tools）"
weight: 4
bookToc: true
---

# 工具（Tools）

## 简介

工具是 LLM 可以调用来执行操作的函数。Pi Mono 提供了定义和处理工具的系统。

## Pi 内置工具

编程代理包含 4 个基本工具：

- **read** — 读取文件
- **write** — 创建/写入文件
- **edit** — 编辑现有文件
- **bash** — 执行 shell 命令

## 在 pi-ai 中创建工具

```typescript
import { Type, Tool } from '@mariozechner/pi-ai';

const calculatorTool: Tool = {
  name: 'calculator',
  description: '执行数学计算',
  parameters: Type.Object({
    expression: Type.String({ description: '数学表达式' }),
  }),
};
```

## 处理工具调用

```typescript
for await (const event of stream(model, ctx, { tools: [calculatorTool] })) {
  if (event.type === 'tool_call') {
    const result = eval(event.args.expression);
    ctx.addToolResult(event.id, String(result));
  }
}
```

## pi-agent-core 中的工具

```typescript
const agent = new Agent({
  initialState: {
    systemPrompt: '你是一个带计算器的助手。',
    model: getModel('anthropic', 'claude-sonnet-4-20250514'),
    tools: [calculatorTool],
  },
});
```

## Pi 扩展

扩展是为编程代理添加新工具的 TypeScript 模块：

```typescript
// .pi/extensions/my-tool.ts
export default {
  name: 'my_tool',
  description: '我的工具',
  parameters: Type.Object({ input: Type.String() }),
  execute: async (args) => {
    return `结果: ${args.input}`;
  },
};
```

## 总结

- 工具让 LLM 执行实际操作
- pi-ai 提供类型化的工具定义系统
- 编程代理通过扩展进行扩展
