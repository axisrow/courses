---
title: "高级设置"
level: 3
lesson: 3
lang: zh
tags: [设置, 钩子, 技能, 扩展, TTSR]
---

# 高级设置

## 介绍

OMP 拥有强大的扩展系统：钩子、技能、自定义命令和工具。

## 钩子 (Hooks)

订阅生命周期事件的 TypeScript 模块：

```typescript
// .omp/hooks/pre/guard-sudo.ts
import type { HookAPI } from "@oh-my-pi/pi-coding-agent/hooks";

export default function (omp: HookAPI) {
  omp.on("tool_call", async (event, ctx) => {
    if (event.toolName === "bash" && /sudo/.test(event.input.command as string)) {
      const ok = await ctx.ui.confirm("允许 sudo？", event.input.command as string);
      if (!ok) return { block: true, reason: "用户阻止" };
    }
    return undefined;
  });
}
```

路径：`~/.omp/agent/hooks/{pre,post}/*.ts`、`.omp/hooks/{pre,post}/*.ts`

## 技能 (Skills)

按需加载的能力包：

```markdown
---
name: brave-search
description: 通过 Brave Search API 进行网络搜索。
---
# Brave Search
...
```

路径：`~/.omp/agent/skills/*/SKILL.md`、`.omp/skills/*/SKILL.md`

## TTSR（时间旅行流式规则）

激活前零上下文消耗的规则：

- 在 `ttsrTrigger` 字段定义正则触发器
- 模型生成匹配文本时 — 流中断，规则注入，请求重试
- 每个规则每会话最多触发一次

## 自定义斜杠命令

`.omp/commands/` 中的 Markdown 文件或 TypeScript。

## 自定义工具

```typescript
// .omp/tools/greet/index.ts
import { Type } from "@sinclair/typebox";
import type { CustomToolFactory } from "@oh-my-pi/pi-coding-agent";

const factory: CustomToolFactory = () => ({
  name: "greet",
  description: "生成问候语",
  parameters: Type.Object({
    name: Type.String({ description: "要问候的名字" }),
  }),
  async execute(_id, params) {
    return { content: [{ type: "text", text: `你好，${(params as any).name}！` }] };
  },
});
export default factory;
```

## 总结

OMP 的扩展系统 — 钩子、技能、TTSR、自定义命令和工具 — 让你可以根据任何工作流定制代理。
