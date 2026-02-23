---
title: "First Run"
level: 1
lesson: 3
language: en
tags: [gsd, first-run, new-project]
---

# First Run

## Introduction

After installing GSD, your first step is creating a project. The `/gsd:new-project` command launches the full initialization cycle.

## Instructions

### 1. Launch Claude Code

```bash
claude --dangerously-skip-permissions
```

> The `--dangerously-skip-permissions` flag is recommended for GSD — otherwise you'll confirm every minor operation.

### 2. Create a Project

```
/gsd:new-project
```

The system goes through 4 stages:
1. **Questions** — asks about your idea, goals, constraints
2. **Research** — spawns parallel agents to investigate the domain
3. **Requirements** — determines what's v1, v2, and out of scope
4. **Roadmap** — creates phases mapped to requirements

### 3. Approve the Roadmap

After creating the roadmap, GSD shows it to you. Approve it — and you're ready to build.

## What Gets Created

```
.planning/
├── PROJECT.md        # Project vision
├── REQUIREMENTS.md   # v1/v2 requirements
├── ROADMAP.md        # Roadmap with phases
├── STATE.md          # Current state
└── research/         # Research results
```

## Examples

```
/gsd:new-project

> I want to build a blog platform with a markdown editor,
> GitHub auth, and Vercel deployment.
```

## Summary

- `/gsd:new-project` is the entry point for any project
- The system asks the right questions automatically
- Creates structure in `.planning/`
- You approve the roadmap before work begins
