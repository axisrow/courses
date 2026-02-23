---
title: "Configuration"
level: 2
lesson: 3
lang: en
tags: [configuration, settings, config.yml]
---

# Configuration

## Introduction

OMP is configured through config files at global and project levels.

## Global Configuration

File: `~/.omp/agent/config.yml`

```yaml
theme:
  dark: titanium
  light: light

modelRoles:
  default: anthropic/claude-sonnet-4-20250514

defaultThinkingLevel: medium

compaction:
  enabled: true
  reserveTokens: 16384
  keepRecentTokens: 20000
  autoContinue: true

skills:
  enabled: true

terminal:
  showImages: true
```

## CLI Management

```bash
omp config list           # All settings
omp config get theme      # Get value
omp config set theme.dark dracula  # Set value
omp config reset theme    # Reset
omp config path           # File path
```

## Project Context Files

OMP loads context from multiple directories: `.omp/`, `.claude/`, `.codex/`, `.gemini/`

Files like `AGENTS.md`, `CLAUDE.md` provide project instructions.

## Custom System Prompt

1. **Project:** `.omp/SYSTEM.md`
2. **Global:** `~/.omp/agent/SYSTEM.md`

```bash
omp --system-prompt "You are a Python expert"
omp --append-system-prompt "Always write tests"
```

## Custom Models

File `~/.omp/agent/models.yml`:

```yaml
providers:
  ollama:
    baseUrl: http://localhost:11434/v1
    api: openai-completions
    models:
      - id: llama-3.1-8b
        name: Llama 3.1 8B
        contextWindow: 128000
        maxTokens: 32000
```

## Themes

65+ built-in themes. Custom: `~/.omp/agent/themes/*.json`.

## Summary

OMP configuration is flexible — from global settings to project contexts and custom models.
