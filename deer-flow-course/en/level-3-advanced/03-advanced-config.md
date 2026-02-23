---
title: "Advanced Configuration"
weight: 3
bookToc: true
---

# Advanced Configuration

## Introduction

In this lesson we'll explore all of DeerFlow's configuration options for advanced use cases.

## Full config.yaml Structure

```yaml
# AI Models
models:
  - name: gpt-4o
    display_name: GPT-4o
    use: langchain_openai:ChatOpenAI
    model: gpt-4o
    api_key: $OPENAI_API_KEY
    max_tokens: 4096
    temperature: 0.7
    supports_vision: true
    supports_thinking: false

# Tools
tools:
  - name: web_search
    group: web
    use: src.community.tavily.tools:web_search_tool

# Tool Groups
tool_groups:
  - name: web
  - name: file:read
  - name: file:write
  - name: bash

# Sandbox
sandbox:
  use: src.sandbox.local:LocalSandboxProvider

# Skills
skills:
  path: ../skills
  container_path: /mnt/skills

# Sub-agents
subagents:
  enabled: true

# Memory
memory:
  enabled: true
  injection_enabled: true
  storage_path: .deer-flow/memory.json
  debounce_seconds: 30
  max_facts: 100
  fact_confidence_threshold: 0.7
  max_injection_tokens: 2000

# Summarization
summarization:
  enabled: true
  trigger:
    type: tokens
    threshold: 100000
  keep:
    recent_messages: 10
```

## Environment Variables

Values starting with `$` are substituted from environment variables:

```yaml
api_key: $OPENAI_API_KEY
```

Configuration priority:
1. Explicit `config_path` argument
2. `DEER_FLOW_CONFIG_PATH` environment variable
3. `config.yaml` in the current directory
4. `config.yaml` in the parent directory (recommended)

## Model Configuration

### Models with Thinking Support

```yaml
models:
  - name: deepseek-v3
    use: langchain_deepseek:ChatDeepSeek
    model: deepseek-chat
    api_key: $DEEPSEEK_API_KEY
    supports_thinking: true
```

### Models with Vision

```yaml
models:
  - name: gpt-4o
    supports_vision: true   # Enables the view_image tool
```

### Local Models

```yaml
models:
  - name: ollama-llama
    display_name: Llama 3 (Local)
    use: langchain_openai:ChatOpenAI
    model: llama3
    base_url: http://localhost:11434/v1
    api_key: ollama
```

## Summarization Settings

Trigger by **tokens**, **messages**, or **fraction** of context window:

```yaml
summarization:
  trigger:
    type: fraction
    threshold: 0.75   # Compress at 75% context usage
```

## MCP Server Configuration

In `extensions_config.json`:

```json
{
  "mcpServers": {
    "filesystem": {
      "enabled": true,
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/tmp"]
    }
  }
}
```

MCP configuration can be updated at runtime via API — LangGraph detects file changes and reloads tools.

## Runtime Configuration

Some parameters can be changed per request:

```json
{
  "configurable": {
    "thinking_enabled": true,
    "model_name": "gpt-4o",
    "is_plan_mode": true,
    "subagent_enabled": true
  }
}
```

## Summary

- `config.yaml` is the central configuration file
- Environment variables supported via `$` prefix
- Models support thinking, vision, and local deployment
- Summarization can be triggered by tokens, messages, or fraction
- MCP servers can be updated at runtime
- Runtime parameters allow per-request behavior changes
