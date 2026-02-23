---
title: "Working Basics"
weight: 5
bookToc: true
---

# Working Basics

## Introduction

In this lesson, we'll learn the core concepts: sessions, context files, and skills.

## Sessions

Pi saves dialog history in sessions. You can:

- Continue a previous conversation
- Branch from any point
- Compact long history to save tokens

```bash
pi --session my-session    # Continue or create a session
pi --sessions              # List sessions
```

## Context Files

`AGENTS.md` and `TOOLS.md` files in your project root are automatically loaded into the agent's context. Use them to give the agent knowledge about your project:

```markdown
# AGENTS.md
This project is a React web application.
Use TypeScript and follow our code style.
```

## Skills

Skills are instruction files that Pi loads when needed. Create a `.pi/skills/` folder:

```bash
mkdir -p .pi/skills
echo "When working with the database, use Prisma ORM" > .pi/skills/database.md
```

## Extensions

Extensions are TypeScript modules that add new tools to the agent. Install them via npm or write your own.

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Ctrl+C` | Cancel/exit |
| `Shift+Ctrl+D` | Debug |
| `Enter` | Send message |

## Summary

- Sessions store dialog history
- AGENTS.md and TOOLS.md set project context
- Skills and extensions let you customize the agent
