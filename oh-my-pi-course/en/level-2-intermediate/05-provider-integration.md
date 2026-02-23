---
title: "Provider Integration"
level: 2
lesson: 5
lang: en
tags: [providers, models, roles, multi-credential]
---

# Provider Integration

## Introduction

OMP supports dozens of AI providers and allows flexible model management.

## Model Roles

```
/model
```

| Role | Purpose |
|------|---------|
| default | Regular work |
| smol | Fast/cheap tasks |
| slow | Deep analysis |
| plan | Planning (/plan) |
| commit | Commits and changelog |

CLI switching:

```bash
omp --model anthropic/claude-sonnet-4
omp --smol anthropic/claude-haiku
omp --slow anthropic/claude-opus
```

Hotkeys: `Ctrl+P` — cycle models, `Ctrl+L` — selector.

## Multi-Credential Support

- Round-robin across API keys
- Automatic fallback on rate limits
- Consistent hashing for stable distribution

## Supported APIs

`openai-completions`, `openai-responses`, `anthropic-messages`, `google-generative-ai`, `google-vertex`, `azure-openai-responses`, `openai-codex-responses`

## Cursor Provider

Use your Cursor Pro subscription:

```
/login
# Select Cursor
```

## Ollama (Local Models)

```yaml
# ~/.omp/agent/models.yml
providers:
  ollama:
    baseUrl: http://localhost:11434/v1
    api: openai-completions
    models:
      - id: llama-3.1-8b
        name: Llama 3.1 8B
        contextWindow: 128000
```

## MCP & Plugins

```bash
omp plugin install <name>
omp plugin enable <name>
omp plugin doctor
```

## Summary

OMP supports many providers with flexible role configuration, multi-credential, and MCP integration.
