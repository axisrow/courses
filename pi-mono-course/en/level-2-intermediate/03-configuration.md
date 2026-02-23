---
title: "Configuration"
weight: 3
bookToc: true
---

# Configuration

## Introduction

Pi offers flexible configuration through config files, environment variables, and commands.

## Environment Variables

Key API key variables:

```bash
export ANTHROPIC_API_KEY=sk-ant-...
export OPENAI_API_KEY=sk-...
export GOOGLE_API_KEY=...
export MISTRAL_API_KEY=...
export GROQ_API_KEY=...
```

## Pi Settings

In interactive mode, use `/settings`:

```
/settings
```

You can configure:
- Default model
- Thinking level
- Theme
- Autocomplete behavior

## Model Selection

```bash
pi --provider anthropic --model claude-sonnet-4-20250514
```

Or interactively:

```
/model anthropic claude-sonnet-4-20250514
```

## Project Context Files

| File | Purpose |
|------|---------|
| `AGENTS.md` | Instructions for the agent about your project |
| `TOOLS.md` | Notes about tools and environment |
| `.pi/skills/` | Skills — context-dependent instructions |

## Themes

Pi supports custom themes for the terminal UI. Themes define colors and component styles.

## Summary

- API keys are set via environment variables
- Settings accessible via /settings and CLI flags
- Context files customize agent behavior
