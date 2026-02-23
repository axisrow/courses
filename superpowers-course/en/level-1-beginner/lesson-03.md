---
title: "How Superpowers Works"
level: 1
lesson: 3
lang: en
---

# How Superpowers Works

## Introduction

The workflow: specification → plan → subagents.

## Stage 1: Brainstorming (Specification)

When you give a task, the agent **doesn't start coding immediately**. It:

1. Asks clarifying questions
2. Explores alternatives
3. Creates a design document
4. Shows it in chunks for review

### Example Dialog

```
You: Build a CLI for task management

Agent: Great idea! Let me clarify:
- Where to store tasks — file, SQLite, cloud?
- Operations: create, delete, mark as done?
- Do you need priorities and tags?
```

## Stage 2: Planning

After spec approval, the agent creates an **implementation plan**:

- Tasks of 2-5 minutes each
- Exact file paths
- Complete code for each task
- Verification steps

## Stage 3: Subagents

The agent launches a **separate subagent** for each task:

1. Subagent receives task context
2. Works with TDD
3. Main agent reviews (two-stage review)
4. Issues → fix or retry

## Summary

- Superpowers works in 3 stages: specification → plan → execution
- The agent always clarifies before starting work
- Plans break work into small tasks
- Subagents execute tasks with review
