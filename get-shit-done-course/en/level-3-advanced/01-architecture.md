---
title: "GSD Architecture"
level: 3
lesson: 1
language: en
tags: [gsd, architecture, system]
---

# GSD Architecture

## Introduction

Under the hood, GSD is an elegant system of slash commands, markdown files, and multi-agent orchestration.

## Instructions

### System Components

```
GSD
├── Slash commands (user interface)
├── Orchestrator (coordination)
├── Sub-agents
│   ├── Researchers (4 parallel)
│   ├── Planner
│   ├── Plan checker
│   ├── Executors (parallel waves)
│   └── Verifier
├── State (.planning/)
│   ├── PROJECT.md
│   ├── REQUIREMENTS.md
│   ├── ROADMAP.md
│   ├── STATE.md
│   ├── config.json
│   └── Phase files
└── Git integration (atomic commits)
```

### Wave Execution

Plans are grouped into "waves" by dependencies:
- **Wave 1**: independent plans → parallel
- **Wave 2**: depends on Wave 1 → wait, then parallel
- **Wave 3**: depends on Wave 2 → and so on

### Sub-agent Lifecycle

1. Orchestrator creates prompt with needed context
2. Sub-agent launches in fresh context window
3. Executes task
4. Returns result to orchestrator
5. Orchestrator integrates and moves forward

### Filesystem as Database

GSD uses no database. All state is markdown files. This gives:
- Version control through git
- Human readability
- Easy debugging
- Portability

## Examples

Typical context usage during phase execution:
```
Main window:     30-40% (orchestration)
Researcher:      20-50% (research)
Planner:         30-60% (planning)
Executor:        40-80% (code)
```

## Summary

- GSD = slash commands + orchestrator + sub-agents + file state
- Wave execution maximizes parallelism
- Each sub-agent gets fresh context
- Files as database — simple, versioned, readable
