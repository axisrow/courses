---
title: "Продвинутые настройки"
level: 3
lesson: 3
lang: ru
tags: [настройки, хуки, навыки, расширения, TTSR]
---

# Продвинутые настройки

## Введение

OMP обладает мощной системой расширений: хуки, навыки, кастомные команды и инструменты.

## Хуки (Hooks)

TypeScript-модули, подписанные на события жизненного цикла:

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

Пути: `~/.omp/agent/hooks/{pre,post}/*.ts`, `.omp/hooks/{pre,post}/*.ts`

## Навыки (Skills)

Пакеты возможностей, загружаемые по запросу:

```markdown
---
name: brave-search
description: Web search via Brave Search API.
---
# Brave Search
...
```

Пути: `~/.omp/agent/skills/*/SKILL.md`, `.omp/skills/*/SKILL.md`

## TTSR (Time Traveling Streamed Rules)

Правила с нулевым потреблением контекста до активации:

- Определяют regex-триггер в поле `ttsrTrigger`
- Когда модель генерирует совпадающий текст — стрим останавливается, правило инжектится, запрос повторяется
- Каждое правило срабатывает максимум один раз за сессию

## Кастомные слэш-команды

Markdown:

```markdown
---
description: Review staged changes
---
Review the staged changes (`git diff --cached`).
```

TypeScript: `.omp/commands/<name>/index.ts`

## Кастомные инструменты

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

## /extensions Dashboard

Интерактивная панель для управления всеми расширениями:

```
/extensions
```

## Итоги

Система расширений OMP — хуки, навыки, TTSR, кастомные команды и инструменты — позволяет адаптировать агента под любые нужды.
