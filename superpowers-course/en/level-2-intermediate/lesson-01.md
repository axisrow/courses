---
title: "Subagent-Driven Development"
level: 2
lesson: 1
lang: en
---

# Subagent-Driven Development

## Introduction

How Superpowers uses subagents for parallel development.

## How Subagents Work

A subagent is a separate coding agent instance that receives:
- Context for one specific task
- TDD instructions
- Acceptance criteria

### Two-Stage Review

After a subagent completes a task:
1. **Spec compliance** — does the result match the plan?
2. **Code quality** — is the code clean, no anti-patterns?

## Benefits

- **Context isolation** — each subagent works with minimal context
- **Parallelism** — multiple subagents can work simultaneously
- **Reliability** — one subagent's error doesn't break everything

## The `dispatching-parallel-agents` Skill

Enables running multiple subagents in parallel for independent tasks.

## Summary

- Subagents work in isolation on specific tasks
- Two-stage review ensures quality
- Parallel subagents speed up development
- The agent can work autonomously for hours
