---
title: "DeerFlow Architecture"
weight: 1
bookToc: true
---

# DeerFlow Architecture

## Introduction

In this lesson we'll look "under the hood" of DeerFlow to understand how the system is built. Knowing the architecture helps you configure, extend, and troubleshoot DeerFlow more effectively.

## Overall Architecture

```
                    ┌──────────────────────────────────────┐
                    │          Nginx (port 2026)            │
                    │        Reverse Proxy                  │
                    └───────┬──────────────────┬───────────┘
                            │                  │
          /api/langgraph/*  │                  │  /api/* (other)
                            ▼                  ▼
           ┌────────────────────┐  ┌────────────────────────┐
           │ LangGraph Server   │  │   Gateway API (8001)   │
           │    (port 2024)     │  │   FastAPI REST         │
           └────────────────────┘  └────────────────────────┘
                    │
           ┌────────────────┐
           │  Lead Agent     │
           │  ├─ Middleware  │
           │  ├─ Tools       │
           │  └─ Subagents   │
           └────────────────┘
```

### Components

| Component | Port | Technology | Purpose |
|-----------|------|------------|---------|
| **Nginx** | 2026 | Nginx | Reverse proxy, single entry point |
| **Frontend** | 3000 | Next.js | Web user interface |
| **Gateway API** | 8001 | FastAPI | REST API for models, MCP, skills, memory |
| **LangGraph Server** | 2024 | LangGraph | Agent execution environment |

### Request Routing

Nginx distributes requests:
- `/api/langgraph/*` → LangGraph Server (agent interaction)
- `/api/*` → Gateway API (configuration management)
- `/` → Frontend (web interface)

## Lead Agent

The main agent is created by `make_lead_agent(config)` and includes:

1. **Dynamic model selection** via `create_chat_model()`
2. **Middleware chain** for request processing
3. **Tool system** via `get_available_tools()`
4. **System prompt** with skills, memory, and instructions

## Middleware Chain

Middleware components process requests sequentially, like filters. Each handles a specific task:

| # | Middleware | Purpose |
|---|-----------|---------|
| 1 | **ThreadDataMiddleware** | Creates directories for each thread |
| 2 | **UploadsMiddleware** | Injects uploaded files into context |
| 3 | **SandboxMiddleware** | Obtains a sandbox for code execution |
| 4 | **DanglingToolCallMiddleware** | Handles incomplete tool calls |
| 5 | **SummarizationMiddleware** | Compresses context when approaching the limit |
| 6 | **TodoListMiddleware** | Tracks tasks in plan mode |
| 7 | **TitleMiddleware** | Generates conversation titles |
| 8 | **MemoryMiddleware** | Sends conversations for memory analysis |
| 9 | **ViewImageMiddleware** | Injects images for vision-capable models |
| 10 | **SubagentLimitMiddleware** | Limits the number of sub-agents |
| 11 | **ClarificationMiddleware** | Intercepts clarification requests (always last) |

### Order Matters!

ClarificationMiddleware **must** be last because it interrupts execution via `Command(goto=END)`.

## Tool System

```python
get_available_tools(groups, include_mcp, model_name, subagent_enabled)
```

Collects tools from multiple sources:

1. **Config-defined** — from `config.yaml` via `resolve_variable()`
2. **MCP** — from enabled MCP servers (lazy initialization, cached)
3. **Built-in** — `present_files`, `ask_clarification`, `view_image`
4. **Subagent** — the `task` tool for delegation

## Reflection System

DeerFlow uses **dynamic module loading**:

```python
# Load a variable from a module
resolve_variable("src.community.tavily.tools:web_search_tool")

# Load a class with type checking
resolve_class("src.sandbox.local:LocalSandboxProvider", SandboxProvider)
```

This lets you configure components via strings in `config.yaml` without changing code.

## Project Structure

```
deer-flow/
├── backend/
│   ├── src/
│   │   ├── agents/           # Agent system
│   │   │   ├── lead_agent/   # Lead agent
│   │   │   ├── middlewares/   # 11 middleware components
│   │   │   ├── memory/        # Memory system
│   │   │   └── thread_state.py
│   │   ├── gateway/           # REST API
│   │   ├── sandbox/           # Sandbox system
│   │   ├── subagents/         # Sub-agent system
│   │   ├── tools/             # Built-in tools
│   │   ├── mcp/               # MCP integration
│   │   ├── models/            # Model factory
│   │   ├── skills/            # Skills system
│   │   ├── config/            # Configuration system
│   │   └── community/         # Community tools
│   └── tests/
├── frontend/                   # Next.js
├── skills/                     # Skills
└── config.yaml                 # Configuration
```

## ThreadState

Each thread (conversation) state:

```python
class ThreadState:
    messages: list          # Message history
    sandbox: str            # Sandbox ID
    thread_data: dict       # Thread data
    title: str              # Title
    artifacts: list         # Artifacts (files)
    todos: list             # Task list
    uploaded_files: list    # Uploaded files
    viewed_images: list     # Viewed images
```

## Summary

- DeerFlow is built on 4 services: Nginx, Frontend, Gateway API, LangGraph
- The lead agent uses a chain of 11 middleware components
- Tools are assembled from configuration, MCP, built-in, and sub-agents
- Dynamic module loading via the reflection system
- Each conversation has isolated state (ThreadState)
