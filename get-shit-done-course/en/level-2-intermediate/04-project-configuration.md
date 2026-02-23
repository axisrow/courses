---
title: "Project Configuration"
level: 2
lesson: 4
language: en
tags: [gsd, configuration, settings]
---

# Project Configuration

## Introduction

GSD is flexibly configurable. You can control the work mode, model profiles, git strategy, and workflow agents.

## Instructions

### Configuration

Settings are stored in `.planning/config.json`. Change via `/gsd:settings`.

### Work Modes

| Setting | Options | Default |
|---------|---------|---------|
| `mode` | `yolo`, `interactive` | `interactive` |
| `depth` | `quick`, `standard`, `comprehensive` | `standard` |

- **yolo** — auto-approve at every step
- **interactive** — requires your confirmation
- **quick/standard/comprehensive** — planning thoroughness

### Model Profiles

```
/gsd:set-profile budget
```

| Profile | Planning | Execution | Verification |
|---------|----------|-----------|--------------|
| `quality` | Opus | Opus | Sonnet |
| `balanced` | Opus | Sonnet | Sonnet |
| `budget` | Sonnet | Sonnet | Haiku |

### Workflow Agents

| Agent | Default | What it does |
|-------|---------|--------------|
| `research` | on | Researches domain before planning |
| `plan_check` | on | Verifies plans before execution |
| `verifier` | on | Confirms results after execution |
| `auto_advance` | off | Auto-chain discuss→plan→execute |

### Git Strategies

| Strategy | What it does |
|----------|--------------|
| `none` | Commits to current branch |
| `phase` | Branch per phase |
| `milestone` | Branch per milestone |

## Examples

```
/gsd:settings
> Set mode=yolo, depth=comprehensive, profile=quality
```

## Summary

- Configuration in `.planning/config.json`
- Three model profiles: quality, balanced, budget
- Modes: yolo (auto) and interactive (manual)
- Git strategies: none, phase, milestone
- Agents can be toggled to save tokens
