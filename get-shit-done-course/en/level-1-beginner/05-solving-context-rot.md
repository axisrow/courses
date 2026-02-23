---
title: "How GSD Solves Context Rot"
level: 1
lesson: 5
language: en
tags: [gsd, context-rot, context-engineering]
---

# How GSD Solves Context Rot

## Introduction

Context rot is the #1 problem when working with AI agents over long sessions. GSD solves it architecturally, not with "better prompts."

## How Context Rot Happens

1. You start a conversation — quality is excellent
2. Context window fills to 50% — quality is fine
3. At 70%+ — model starts "forgetting" earlier decisions
4. At 90%+ — responses degrade, code breaks

## How GSD Solves This

### 1. Fresh Context Per Task

Each plan runs in a separate sub-agent with clean 200k tokens. Nothing extra — just the task and needed context.

### 2. File-based State Instead of Conversation Memory

```
PROJECT.md       → What we're building (always loaded)
REQUIREMENTS.md  → What needs to be done
ROADMAP.md       → Where we are in the process
STATE.md         → Current decisions and blockers
PLAN.md          → Specific task with XML structure
```

### 3. Wave Execution

Independent tasks run in parallel, dependent ones run sequentially. No agent gets overloaded.

### 4. Atomic Commits

Each task = one commit. If something breaks — revert one commit, don't untangle a mess.

## Examples

**Without GSD:**
```
Message 1:  "Create API" → excellent
Message 15: "Add auth" → okay
Message 40: "Fix bug" → forgot half the architecture
```

**With GSD:**
```
Phase 1, Plan 1: API endpoints → fresh context → excellent
Phase 1, Plan 2: Auth → fresh context → excellent
Phase 2, Plan 1: Bug fix → fresh context → excellent
```

## Summary

- Context rot is inevitable in long conversations
- GSD solves it with fresh contexts per task
- State lives in files, not conversation memory
- Atomic commits give clean history
- Quality stays consistent regardless of project size
