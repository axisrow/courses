---
title: "Installing GSD"
level: 1
lesson: 2
language: en
tags: [gsd, installation, npx]
---

# Installing GSD

## Introduction

GSD installs with a single npx command. No need to clone repos or manage dependencies.

## Instructions

### Quick Install

```bash
npx get-shit-done-cc@latest
```

The installer asks:
1. **Runtime** — Claude Code, OpenCode, Gemini, or all
2. **Location** — Global (all projects) or local (current project)

### Non-interactive Install

```bash
npx get-shit-done-cc --claude --global    # Claude Code globally
npx get-shit-done-cc --opencode --global  # OpenCode globally
npx get-shit-done-cc --gemini --global    # Gemini CLI globally
npx get-shit-done-cc --all --global       # All runtimes
```

### Verify Installation

Open Claude Code and type:

```
/gsd:help
```

If you see a list of commands — you're good.

## Examples

```bash
# Install for Claude Code in current project
npx get-shit-done-cc --claude --local

# Update to latest version
npx get-shit-done-cc@latest
```

## Summary

- Install via `npx get-shit-done-cc@latest`
- Choose runtime and location (global/local)
- Verify with `/gsd:help`
- Update with the same command using `@latest`
