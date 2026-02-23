---
title: "Debugging and Optimization"
level: 3
lesson: 4
lang: en
---

# Debugging and Optimization

## Introduction

Systematic debugging and agent workflow optimization.

## Systematic Debugging

The `systematic-debugging` skill uses a 4-phase process:

### Phase 1: Reproduce
Create a minimal reproducible example.

### Phase 2: Isolate
Narrow the search area. Use binary search across commits.

### Phase 3: Root Cause
Find the **real** cause, not the symptom.

### Phase 4: Fix
Write a test reproducing the bug, fix with minimal change, verify.

## verification-before-completion

Won't let the agent declare "done" without evidence:
- All tests pass
- New tests cover changes
- No regressions

## Agent Optimization

- **Reduce context** — smaller tasks = more accurate results
- **Improve plans** — add detail to problematic tasks
- **Update AGENTS.md** — add rules as you discover issues

## Summary

- Systematic debugging: 4 phases from reproduction to fix
- Always write a test for the bug before fixing
- Optimize through context reduction and plan improvement
- AGENTS.md is a living document
