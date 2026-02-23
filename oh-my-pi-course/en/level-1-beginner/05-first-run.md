---
title: "First Run"
level: 1
lesson: 5
lang: en
tags: [getting started, first run, models]
---

# First Run

## Introduction

You've installed OMP and configured an API key. Let's launch the agent and try the basic features.

## Launch

```bash
omp
```

You'll see a welcome screen with logo and tips.

## Configure Model Roles

Use `/model` to assign models:

- **default** — regular work
- **smol** — fast/cheap tasks
- **slow** — deep analysis
- **plan** — planning
- **commit** — commit generation

## First Steps

### Chat with the agent

```
> What files are in the current directory?
```

### Reference files with @

```
> Explain @src/main.ts
```

### Run a command

```
> !git status
```

(`!` prefix runs the command and includes output in context.)

### Try plan mode

```
/plan
> Plan a refactor of the auth module
```

## Session Management

```bash
omp -c              # Continue last session
omp -r              # Pick a session
omp --no-session    # Don't save
```

## Useful Slash Commands

| Command | Description |
|---------|-------------|
| `/model` | Model selector |
| `/plan` | Plan mode |
| `/settings` | Settings |
| `/extensions` | Extensions & context |
| `/compact` | Compress context |
| `/export` | Export to HTML |
| `/exit` | Exit |

## Summary

You've launched OMP, configured a model, and tried the basic features. The next level covers advanced tools.
