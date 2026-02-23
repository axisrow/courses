---
title: "What is Oh My Pi"
level: 1
lesson: 1
lang: en
tags: [introduction, overview]
---

# What is Oh My Pi

## Introduction

Oh My Pi (OMP) is an AI coding agent that runs directly in your terminal. It's a fork of [pi-mono](https://github.com/badlogic/pi-mono) by Mario Zechner, extended by Can Bölük.

## What It Offers

OMP is a full-featured environment for AI-assisted coding from the command line:

- **Interactive terminal UI** — chat with AI in your terminal
- **Built-in tools** — file editing, search, grep, bash, Python, browser
- **Session branching** — save and return to any point in a conversation
- **Extensibility** — custom commands, hooks, skills, tools
- **Many providers** — Anthropic, OpenAI, Google, xAI, Groq, and dozens more

## Key Differences from pi-mono

OMP adds on top of pi-mono:

- **Hashline editing** — unique hash anchors per line, no "string not found" errors
- **Native Rust engine** — 7,500 lines of Rust for grep, shell, syntax highlighting
- **LSP integration** — 40+ languages with formatting and diagnostics
- **Commit Tool** — AI-powered commits with hunk-level staging
- **Python Tool** — persistent IPython kernel with helpers
- **TTSR** — rules that fire only when needed (zero context until activation)
- **Subagents** — parallel task execution
- **65+ themes**

## Quick Example

```bash
omp
> List all .ts files in src/
```

## Summary

Oh My Pi is a powerful terminal AI agent built on pi-mono with many enhancements. In the next lessons we'll install it and get started.
