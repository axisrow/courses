---
title: "Working with Different Agents"
level: 2
lesson: 5
language: en
tags: [gsd, claude-code, opencode, gemini]
---

# Working with Different Agents

## Introduction

GSD supports three runtimes: Claude Code, OpenCode, and Gemini CLI. Installation and commands are the same — only the execution environment differs.

## Instructions

### Supported Runtimes

| Runtime | Description | Flag |
|---------|-------------|------|
| **Claude Code** | Primary, by Anthropic | `--claude` |
| **OpenCode** | Open source, free models | `--opencode` |
| **Gemini CLI** | Google Gemini | `--gemini` |

### Install for Specific Runtime

```bash
npx get-shit-done-cc --claude --global
npx get-shit-done-cc --opencode --global
npx get-shit-done-cc --gemini --global
npx get-shit-done-cc --all --global       # All three
```

### File Locations

| Runtime | Global path |
|---------|-------------|
| Claude Code | `~/.claude/` |
| OpenCode | `~/.config/opencode/` |
| Gemini | `~/.gemini/` |

### Differences

Core GSD logic is identical across runtimes. Differences:
- **Models** — each runtime uses its own models
- **Commands** — slash command syntax may vary slightly
- **Sub-agents** — parallelism implementation depends on runtime

## Examples

```bash
npx get-shit-done-cc --all --global

# Verify in Claude Code
claude
/gsd:help

# Verify in OpenCode
opencode
/gsd:help
```

## Summary

- GSD works in Claude Code, OpenCode, and Gemini CLI
- Single install command with runtime flags
- Logic and commands are the same
- Can install for all runtimes at once
