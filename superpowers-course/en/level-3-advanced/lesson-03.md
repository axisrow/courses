---
title: "Advanced Workflows"
level: 3
lesson: 3
lang: en
---

# Advanced Workflows

## Introduction

Complex workflows: parallel agents, code review, git worktrees.

## Git Worktrees

The `using-git-worktrees` skill creates isolated workspaces:

```bash
git worktree add ../project-feature-x feature-x
```

Benefits: main branch untouched, parallel features, clean test baseline.

## Parallel Agents

`dispatching-parallel-agents` enables:
1. Identify independent tasks
2. Launch a subagent for each
3. Collect results
4. Verify compatibility

## Code Review Workflow

Two-stage process:
- **requesting-code-review** — pre-review checklist, auto-test, linting
- **receiving-code-review** — handle feedback, severity classification, critical issues block

## Finishing Workflow

`finishing-a-development-branch`: verify tests → choose merge/PR/keep/discard → cleanup worktree.

## Summary

- Git worktrees provide isolation
- Parallel agents speed up work
- Code review is mandatory
- Workflows can be flexibly combined
