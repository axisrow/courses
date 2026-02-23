---
title: "Sub-Agents"
weight: 1
bookToc: true
---

# Sub-Agents

## Introduction

One of DeerFlow's most powerful features is **sub-agents**. Imagine a project manager who can hire helpers to work on different parts of a task in parallel. That's exactly how the sub-agent system works.

## How the Sub-Agent System Works

### Lead Agent

The **lead agent** is DeerFlow's "brain." It receives your task and decides whether to bring in helpers. For complex tasks, it breaks them into subtasks and creates sub-agents.

### Sub-Agents

A **sub-agent** is a separate AI helper that:
- Works in an **isolated context** (can't see what others are doing)
- Has its own set of **tools**
- Executes **one specific subtask**
- Returns a **structured result** to the lead agent

### Built-in Sub-Agent Types

| Type | Description | Tools |
|------|-------------|-------|
| `general-purpose` | Universal helper | All except delegation |
| `bash` | Command specialist | Only bash commands |

## How It Works

```
Your request: "Compare React, Vue, and Angular"
            ↓
Lead agent creates 3 sub-agents:
  ├─ Sub-agent 1: researches React     ← work in
  ├─ Sub-agent 2: researches Vue        ← parallel
  └─ Sub-agent 3: researches Angular    ← (simultaneously!)
            ↓
Results collected → final comparison
```

## Limitations

- **Maximum 3 sub-agents** simultaneously (configurable)
- **15-minute timeout** per sub-agent
- Sub-agents **cannot** create their own sub-agents (single level only)

## The `task` Tool

The lead agent delegates via the `task` tool:

```
task(
  description="Research React",
  prompt="Find information about React...",
  subagent_type="general-purpose",
  max_turns=10
)
```

## Enabling Sub-Agents

In `config.yaml`:

```yaml
subagents:
  enabled: true
```

## Sub-Agent Lifecycle

1. **task_started** — sub-agent created and working
2. **task_running** — executing (updates every 5 seconds)
3. **task_completed** — finished successfully
4. **task_failed** — error occurred
5. **task_timed_out** — time expired (15 minutes)

All events are displayed in the interface in real time.

## Practical Example

Try this:

```
I need a full overview of three databases: PostgreSQL, MongoDB, and Redis.
For each: description, strengths/weaknesses, typical use cases,
and a Python connection example.
Then create a comparison table.
```

## Summary

- Sub-agents enable parallel task execution
- Each sub-agent works in an isolated context
- Maximum 3 simultaneous sub-agents, 15-minute timeout
- Built-in types: `general-purpose` and `bash`
- The lead agent coordinates sub-agents and collects results
