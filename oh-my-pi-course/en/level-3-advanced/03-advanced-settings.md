---
title: "Advanced Settings"
level: 3
lesson: 3
lang: en
tags: [settings, hooks, skills, extensions, TTSR]
---

# Advanced Settings

## Introduction

OMP has a powerful extension system: hooks, skills, custom commands, and tools.

## Hooks

TypeScript modules subscribing to lifecycle events:

```typescript
// .omp/hooks/pre/guard-sudo.ts
import type { HookAPI } from "@oh-my-pi/pi-coding-agent/hooks";

export default function (omp: HookAPI) {
  omp.on("tool_call", async (event, ctx) => {
    if (event.toolName === "bash" && /sudo/.test(event.input.command as string)) {
      const ok = await ctx.ui.confirm("Allow sudo?", event.input.command as string);
      if (!ok) return { block: true, reason: "Blocked by user" };
    }
    return undefined;
  });
}
```

Paths: `~/.omp/agent/hooks/{pre,post}/*.ts`, `.omp/hooks/{pre,post}/*.ts`

## Skills

Capability packages loaded on demand:

```markdown
---
name: brave-search
description: Web search via Brave Search API.
---
# Brave Search
...
```

Paths: `~/.omp/agent/skills/*/SKILL.md`, `.omp/skills/*/SKILL.md`

## TTSR (Time Traveling Streamed Rules)

Zero context-cost rules until activation:

- Define a regex trigger in `ttsrTrigger` field
- When the model generates matching text — stream aborts, rule injects, request retries
- Each rule fires at most once per session

## Custom Slash Commands

Markdown files or TypeScript in `.omp/commands/`.

## Custom Tools

```typescript
// .omp/tools/greet/index.ts
import { Type } from "@sinclair/typebox";
import type { CustomToolFactory } from "@oh-my-pi/pi-coding-agent";

const factory: CustomToolFactory = () => ({
  name: "greet",
  description: "Generate a greeting",
  parameters: Type.Object({
    name: Type.String({ description: "Name to greet" }),
  }),
  async execute(_id, params) {
    return { content: [{ type: "text", text: `Hello, ${(params as any).name}!` }] };
  },
});
export default factory;
```

## Summary

OMP's extension system — hooks, skills, TTSR, custom commands and tools — lets you adapt the agent to any workflow.
