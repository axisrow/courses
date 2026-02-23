---
title: "Инструменты (Tools)"
weight: 4
bookToc: true
---

# Инструменты (Tools)

## Введение

Инструменты — это функции, которые LLM может вызывать для выполнения действий. Pi Mono предоставляет систему определения и обработки инструментов.

## Встроенные инструменты Pi

Coding agent включает 4 базовых инструмента:

- **read** — чтение файлов
- **write** — создание/запись файлов
- **edit** — редактирование существующих файлов
- **bash** — выполнение shell-команд

## Создание инструмента в pi-ai

```typescript
import { Type, Tool } from '@mariozechner/pi-ai';

const calculatorTool: Tool = {
  name: 'calculator',
  description: 'Выполняет математические вычисления',
  parameters: Type.Object({
    expression: Type.String({ description: 'Математическое выражение' }),
  }),
};
```

## Обработка вызовов инструментов

```typescript
for await (const event of stream(model, ctx, { tools: [calculatorTool] })) {
  if (event.type === 'tool_call') {
    const result = eval(event.args.expression);
    ctx.addToolResult(event.id, String(result));
  }
}
```

## Инструменты в pi-agent-core

```typescript
const agent = new Agent({
  initialState: {
    systemPrompt: 'Ты помощник с калькулятором.',
    model: getModel('anthropic', 'claude-sonnet-4-20250514'),
    tools: [calculatorTool],
  },
});
```

## Расширения Pi

Расширения — это TypeScript-модули, которые добавляют новые инструменты в coding agent:

```typescript
// .pi/extensions/my-tool.ts
export default {
  name: 'my_tool',
  description: 'Мой инструмент',
  parameters: Type.Object({ input: Type.String() }),
  execute: async (args) => {
    return `Результат: ${args.input}`;
  },
};
```

## Итоги

- Инструменты позволяют LLM выполнять реальные действия
- pi-ai предоставляет типизированную систему определения инструментов
- Coding agent расширяется через Extensions
