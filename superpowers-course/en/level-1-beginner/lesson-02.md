---
title: "Installing Superpowers"
level: 1
lesson: 2
lang: en
---

# Installing Superpowers

## Introduction

How to install Superpowers in Claude Code, Cursor, Codex, and OpenCode.

## Installation

### Claude Code (Recommended)

Claude Code has a built-in plugin marketplace.

```bash
# Step 1: Add the marketplace
/plugin marketplace add obra/superpowers-marketplace

# Step 2: Install the plugin
/plugin install superpowers@superpowers-marketplace
```

### Cursor

In Cursor Agent chat:

```
/plugin-add superpowers
```

### Codex

Tell Codex:

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

### OpenCode

Tell OpenCode:

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md
```

## Verify Installation

Start a new session and ask the agent to plan something:

```
Help me plan a new feature
```

If Superpowers is working, the agent will start asking clarifying questions instead of jumping into code.

## Updating

```bash
/plugin update superpowers
```

## Summary

- Installation depends on the platform
- Claude Code and Cursor — via marketplace
- Codex and OpenCode — via manual instructions
- Verify by asking the agent to plan a feature
