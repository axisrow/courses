---
title: "Project Customization"
level: 2
lesson: 4
lang: en
---

# Project Customization

## Introduction

Adapting Superpowers for your specific project and team.

## AGENTS.md

The `AGENTS.md` file in your project root is your main customization method:

```markdown
# AGENTS.md

## Tech Stack
- TypeScript, Node.js 20
- PostgreSQL, Prisma ORM
- Jest for testing

## Conventions
- All files in src/
- Tests alongside code: src/foo.ts → src/foo.test.ts
- Use ESM

## Forbidden
- No `any` types
- No console.log for debugging
```

## Adapting Skills

Influence skill behavior through project context:
- Add examples of good code
- Document architectural decisions
- Specify testing frameworks

## Working with Existing Code

1. Ensure tests pass (`npm test`)
2. Agent uses git worktrees for isolation
3. Existing code becomes context for new tasks

## Summary

- AGENTS.md is the main configuration file
- Describe stack, conventions, and restrictions
- Superpowers adapts to your project
- Existing tests and code become context
