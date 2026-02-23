---
title: "Differences from pi-mono"
level: 3
lesson: 2
lang: en
tags: [pi-mono, fork, differences, comparison]
---

# Differences from pi-mono

## Introduction

OMP is a fork of pi-mono with substantial additions. Let's examine the key differences.

## New Tools

| Feature | pi-mono | OMP |
|---------|---------|-----|
| Hashline editing | ❌ | ✅ |
| Commit Tool (AI commits) | ❌ | ✅ |
| Python Tool (IPython) | ❌ | ✅ |
| LSP integration (40+ langs) | ❌ | ✅ |
| TTSR (triggered rules) | ❌ | ✅ |
| Task Tool (subagents) | ❌ | ✅ |
| Code Review (/review) | ❌ | ✅ |
| Todo Tool | ❌ | ✅ |
| Ask Tool | ❌ | ✅ |
| Browser (14 stealth scripts) | ❌ | ✅ |
| SSH Tool | ❌ | ✅ |
| Image Generation | ❌ | ✅ |

## Native Engine

pi-mono uses external utilities (ripgrep, bash). OMP includes 7,500 lines of Rust N-API for built-in grep, shell, syntax highlighting, and other modules.

## Universal Config Discovery

OMP loads configuration from 8 tools: Claude Code, Cursor, Windsurf, Gemini, Codex, Cline, GitHub Copilot, VS Code.

## Extended Provider Support

- More providers (30+)
- Multi-credential with round-robin
- Cursor Provider
- Model roles (smol, slow, plan, commit)

## TUI

- 65+ themes
- Powerline footer with status
- Auto session titles
- LSP status in the interface
- Todo panel (Ctrl+T)

## Summary

OMP significantly extends pi-mono: hashline, native engine, subagents, LSP, dozens of new tools and providers.
