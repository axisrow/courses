---
title: "OAuth & API Keys"
level: 1
lesson: 4
lang: en
tags: [api, oauth, providers, authentication]
---

# OAuth & API Keys

## Introduction

OMP needs access to an AI provider. There are two methods: environment variables and interactive `/login`.

## Method 1: Environment Variables

Export the key for your provider:

```bash
# Anthropic (Claude)
export ANTHROPIC_API_KEY="sk-ant-..."

# OpenAI
export OPENAI_API_KEY="sk-..."

# Google Gemini
export GEMINI_API_KEY="..."

# xAI (Grok)
export XAI_API_KEY="..."

# OpenRouter (access many models)
export OPENROUTER_API_KEY="..."
```

Add the line to `~/.bashrc` or `~/.zshrc` for persistence.

## Method 2: Interactive /login

```bash
omp
/login
```

Supported OAuth providers include: Anthropic, ChatGPT, GitHub Copilot, Google Cloud, Cursor, Perplexity, Ollama, and many more.

## Credential Behavior

- `/login` **appends** credentials (doesn't wipe existing ones)
- `/logout` clears credentials for the selected provider
- Credentials stored in `~/.omp/agent/agent.db`
- API keys take priority over OAuth

## Local Models (Ollama)

```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama pull llama3.1
omp
/login
# Select ollama
```

API key for Ollama is optional.

## Summary

Configure an API key via environment variable or `/login`. You can use multiple providers simultaneously.
