---
title: "Recommended Models"
weight: 5
bookToc: true
---

# Recommended Models

## Introduction

DeerFlow is **model-agnostic** — it works with any AI model supporting the OpenAI-compatible API. But not all models are equally good for agent tasks.

## What Matters for Agent Tasks

1. **Long context window** (100K+ tokens) — agents work with large volumes of information
2. **Reasoning capabilities** — planning, task decomposition, decision-making
3. **Multimodality** — image understanding for charts, screenshots, photos
4. **Reliable tool use** — stable, correct function calling

## Recommended Models

### Top Picks

| Model | Provider | Context | Reasoning | Vision | Tool Use |
|-------|----------|---------|-----------|--------|----------|
| GPT-4o | OpenAI | 128K | ✅ | ✅ | ✅✅ |
| Claude 3.5 Sonnet | Anthropic | 200K | ✅ | ✅ | ✅✅ |
| DeepSeek V3 | DeepSeek | 128K | ✅ | ✅ | ✅ |

### Budget Options

| Model | Provider | Price |
|-------|----------|-------|
| GPT-4o-mini | OpenAI | Low |
| Claude 3 Haiku | Anthropic | Low |
| DeepSeek V3 | DeepSeek | Very low |

## Configuration Examples

### OpenAI
```yaml
models:
  - name: gpt-4o
    display_name: GPT-4o
    use: langchain_openai:ChatOpenAI
    model: gpt-4o
    api_key: $OPENAI_API_KEY
    supports_vision: true
```

### Anthropic
```yaml
models:
  - name: claude-sonnet
    display_name: Claude 3.5 Sonnet
    use: langchain_anthropic:ChatAnthropic
    model: claude-3-5-sonnet-20241022
    api_key: $ANTHROPIC_API_KEY
    supports_vision: true
```

### Local Models
```yaml
models:
  - name: local-model
    display_name: Local LLM
    use: langchain_openai:ChatOpenAI
    model: my-model
    base_url: http://localhost:8080/v1
    api_key: not-needed
```

## Choosing Models for Tasks

| Task | Recommendation |
|------|---------------|
| Research | GPT-4o, Claude Sonnet |
| Code generation | GPT-4o, DeepSeek V3 |
| Image analysis | GPT-4o (supports_vision) |
| Simple tasks | GPT-4o-mini, DeepSeek V3 |
| Long conversations | Claude Sonnet (200K context) |

## Summary

- DeerFlow works with any OpenAI-compatible model
- For agent tasks: long context, reasoning, and tool use matter most
- GPT-4o and Claude Sonnet are top picks
- DeepSeek V3 is an excellent budget option
- Local models can be connected via OpenAI-compatible API

🎉 Level 2 complete! Move on to Level 3 for a deep dive into DeerFlow's architecture.
