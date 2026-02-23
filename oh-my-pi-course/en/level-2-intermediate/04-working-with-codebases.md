---
title: "Working with Codebases"
level: 2
lesson: 4
lang: en
tags: [code, sessions, branching, context]
---

# Working with Codebases

## Introduction

OMP excels at navigating and editing large projects.

## File References

```
> Explain @src/auth/middleware.ts
> Compare @old.ts and @new.ts
```

Supports @ + Tab for autocomplete respecting `.gitignore`.

## Bash Mode

```
> !git log --oneline -10
> !find src -name "*.test.ts" | head -20
```

`!!` — execute without adding to model context.

## Session Management

Sessions stored in `~/.omp/agent/sessions/` as JSONL.

```bash
omp -c                    # Continue last
omp -r                    # Pick from list
omp -r abc123             # By ID prefix
omp --no-session          # Don't save
```

## Session Branching

- `/tree` — navigate session tree
- `/branch` — branch from a past message
- `/fork` — fork the session

## Context Compaction

```
/compact                    # Manual compaction
/compact Focus on the API   # With focus hint
```

Auto-compaction is configurable in settings.

## Plan Mode

```
/plan
> Plan the database migration from PostgreSQL to SQLite
```

## Code Review

```
/review
```

Interactive selection: branch comparison, uncommitted changes, commit review.

## Summary

OMP provides a full toolkit for navigation, editing, and session management in large projects.
