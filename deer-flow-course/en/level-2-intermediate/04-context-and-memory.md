---
title: "Context & Memory"
weight: 4
bookToc: true
---

# Context & Memory

## Introduction

Most chatbots forget everything when you close the window. DeerFlow doesn't. It has two mechanisms: **context management** (within a session) and **long-term memory** (across sessions).

## Context (Within a Session)

### The Context Window Problem

Every AI model has a limit on text — the **context window** (e.g., 128,000 tokens ≈ 96,000 words). If a conversation gets too long, old messages "fall off."

### How DeerFlow Solves This

#### 1. Isolated Sub-Agent Context
Each sub-agent works in its own context, invisible to others. This saves context space.

#### 2. Summarization
When context approaches the limit, DeerFlow automatically compresses old messages into a summary.

```yaml
summarization:
  enabled: true
  trigger:
    type: tokens
    threshold: 100000
  keep:
    recent_messages: 10
```

#### 3. Offloading to the File System
Intermediate sub-agent results are saved to files rather than kept in context.

## Long-Term Memory (Across Sessions)

### How Memory Works

DeerFlow **automatically extracts** important information from conversations and saves it. Next time, this information is included in the system prompt.

### What Gets Remembered

Stored in `memory.json`:

- **User Context**: work context, personal context, top of mind
- **History**: recent months, earlier context, long-term background
- **Facts**: discrete items with content, category, and confidence score

### Fact Categories

| Category | Example |
|----------|---------|
| `preference` | "Prefers concise answers" |
| `knowledge` | "Knows Python and JavaScript" |
| `context` | "Works at a startup" |
| `behavior` | "Often asks for code examples" |
| `goal` | "Wants to learn Go" |

### Memory Configuration

```yaml
memory:
  enabled: true
  injection_enabled: true
  storage_path: .deer-flow/memory.json
  debounce_seconds: 30
  max_facts: 100
  fact_confidence_threshold: 0.7
  max_injection_tokens: 2000
```

### How Memory Updates

1. You chat with DeerFlow
2. **MemoryMiddleware** selects important messages
3. After 30 seconds (debounce), analysis runs
4. AI extracts facts and context
5. Updates `memory.json` atomically
6. Next interaction — information is already in the prompt

### Memory API

- `GET /api/memory` — view current memory
- `POST /api/memory/reload` — force reload
- `GET /api/memory/status` — system status

## Summary

- Context is managed through sub-agent isolation and summarization
- Long-term memory saves facts, preferences, and context
- Memory updates automatically in the background
- Stored locally in `memory.json` under your control
- Configurable via `config.yaml` and manageable via API
