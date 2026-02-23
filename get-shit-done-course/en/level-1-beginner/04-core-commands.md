---
title: "Core GSD Commands"
level: 1
lesson: 4
language: en
tags: [gsd, commands, workflow]
---

# Core GSD Commands

## Introduction

GSD works through slash commands inside Claude Code (or similar runtime). The main cycle: discuss → plan → execute → verify.

## Instructions

### Main Cycle

| Command | What it does |
|---------|--------------|
| `/gsd:new-project` | Create project from scratch |
| `/gsd:discuss-phase N` | Discuss phase details before planning |
| `/gsd:plan-phase N` | Research and create plan |
| `/gsd:execute-phase N` | Execute plan in parallel waves |
| `/gsd:verify-work N` | Manual result verification |

### Navigation

| Command | What it does |
|---------|--------------|
| `/gsd:progress` | Show current status |
| `/gsd:help` | List all commands |

### Quick Tasks

```
/gsd:quick
> Add a dark mode toggle to settings
```

For tasks that don't need full planning.

### Phase Management

| Command | What it does |
|---------|--------------|
| `/gsd:add-phase` | Add a phase |
| `/gsd:insert-phase N` | Insert an urgent phase |
| `/gsd:remove-phase N` | Remove a phase |

### Sessions

| Command | What it does |
|---------|--------------|
| `/gsd:pause-work` | Save progress |
| `/gsd:resume-work` | Restore progress |

## Examples

```
/gsd:discuss-phase 1
/gsd:plan-phase 1
/gsd:execute-phase 1
/gsd:verify-work 1

/gsd:discuss-phase 2
...

/gsd:complete-milestone
```

## Summary

- Main cycle: discuss → plan → execute → verify
- `/gsd:quick` for small tasks
- `/gsd:progress` to see where you are
- `/gsd:pause-work` and `/gsd:resume-work` for sessions
