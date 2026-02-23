---
title: "Context Engineering"
level: 2
lesson: 2
language: en
tags: [gsd, context-engineering, files]
---

# Context Engineering

## Introduction

Context engineering is the art of giving AI exactly the context it needs. Not more, not less. GSD does this automatically.

## Instructions

### Context Hierarchy in GSD

| File | Role | When loaded |
|------|------|-------------|
| `PROJECT.md` | Project vision | Always |
| `STATE.md` | Current state, decisions | Always |
| `ROADMAP.md` | Progress | During planning |
| `REQUIREMENTS.md` | Requirements | During planning |
| `CONTEXT.md` | Phase decisions | During phase planning |
| `RESEARCH.md` | Research findings | During planning |
| `PLAN.md` | Specific task | During execution |

### Size Limits

GSD controls file sizes — not for convenience, but because Claude's quality degrades with large contexts. Each file is size-optimized.

### "Need to Know" Principle

The executor doesn't see all research and all plans. It sees only:
- PROJECT.md — project understanding
- Its specific PLAN.md — what to do
- STATE.md — current decisions

This gives it clean 200k tokens for work.

## Examples

Bad context:
```
"Remember, 30 messages ago we decided to use PostgreSQL?"
```

Good context (GSD):
```
STATE.md: database=PostgreSQL, orm=Prisma, deployed=Vercel
```

## Summary

- Context engineering = right context at the right moment
- Each agent receives only the files it needs
- File sizes are controlled for optimal quality
- State lives in files, not conversation memory
