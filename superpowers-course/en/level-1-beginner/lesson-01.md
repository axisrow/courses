---
title: "What is Superpowers"
level: 1
lesson: 1
lang: en
---

# What is Superpowers

## Introduction

Introduction to Superpowers — an agentic skills framework for coding agents.

Superpowers is a framework by Jesse Vincent (obra) that turns an ordinary coding agent into a systematic developer. Instead of chaotic code generation, the agent follows a clear process: first understand the task, then design the solution, then write code.

## What is Superpowers

Superpowers is a set of **skills** that automatically activate in your coding agent. Skills are instructions that guide the agent at every development stage.

### Key Principles

- **Test-Driven Development** — tests first, always
- **Systematic over ad-hoc** — process over guessing
- **Complexity reduction** — simplicity as primary goal
- **Evidence over claims** — verify before declaring success

### Core Workflow

1. **Brainstorming** — agent clarifies the task, asks questions
2. **Specification** — formalizes requirements into a document
3. **Plan** — breaks work into 2-5 minute tasks
4. **Subagents** — launches separate agents for each task
5. **Code Review** — reviews the result
6. **Finish** — merges or creates PR

### Available Skills

| Category | Skills |
|----------|--------|
| Testing | test-driven-development |
| Debugging | systematic-debugging, verification-before-completion |
| Collaboration | brainstorming, writing-plans, executing-plans, subagent-driven-development |
| Git | using-git-worktrees, finishing-a-development-branch |
| Meta | writing-skills, using-superpowers |

## Example

You tell the agent: "Build a REST API for notes." Without Superpowers, the agent would start coding immediately. With Superpowers:

1. Agent asks: "What fields does a note have? Do you need auth? Which database?"
2. Shows specification in digestible chunks
3. Creates a plan of 10-15 tasks
4. Executes each task via subagent with TDD

## Summary

- Superpowers is a skills framework for coding agents
- Skills activate automatically
- Core flow: specification → plan → subagents → TDD
- Works with Claude Code, Cursor, Codex, OpenCode
