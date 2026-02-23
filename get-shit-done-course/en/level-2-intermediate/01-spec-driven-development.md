---
title: "Spec-driven Development"
level: 2
lesson: 1
language: en
tags: [gsd, spec-driven, requirements]
---

# Spec-driven Development

## Introduction

GSD is built on spec-driven development: specification first, code second. Instead of "make me a website," you get structured requirements, a roadmap, and plans.

## Instructions

### Specification Structure

GSD automatically creates:

1. **PROJECT.md** — high-level vision
2. **REQUIREMENTS.md** — concrete requirements split into v1/v2/out-of-scope
3. **ROADMAP.md** — phases mapped to requirements

### How It Works

```
Your idea → Questions → Research → Requirements → Roadmap → Plans → Code
```

Each step narrows uncertainty. By the time code is written, the AI knows exactly what to do.

### Plans in XML

```xml
<task type="auto">
  <name>Create login endpoint</name>
  <files>src/api/auth/login.ts</files>
  <action>
    Use jose for JWT.
    Validate credentials.
    Return httpOnly cookie.
  </action>
  <verify>curl POST /api/auth/login → 200 + cookie</verify>
  <done>Valid credentials → cookie, invalid → 401</done>
</task>
```

## Examples

```
/gsd:new-project

> I want a task management SaaS with teams,
> kanban board, and Slack integration.

GSD creates:
- PROJECT.md with vision
- REQUIREMENTS.md with ~15-20 concrete requirements
- ROADMAP.md with 4-6 phases
```

## Summary

- Spec-driven = specification before code
- GSD auto-generates PROJECT, REQUIREMENTS, ROADMAP
- Each plan is an XML structure with task and verification
- Uncertainty is eliminated before writing code
