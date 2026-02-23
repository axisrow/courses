---
title: "Optimized Tools"
level: 2
lesson: 2
lang: en
tags: [tools, python, lsp, commit, browser]
---

# Optimized Tools

## Introduction

OMP includes a set of powerful built-in tools that go far beyond the basics.

## Commit Tool

AI-powered commit generation with change analysis:

```bash
omp commit              # Interactive mode
omp commit --push       # Commit + push
omp commit --dry-run    # Preview
```

Features: split commits, hunk-level staging, changelog generation.

## Python Tool

Persistent IPython kernel:

```bash
omp setup python  # Install dependencies
```

Helpers: `lines()`, `insert_at()`, `delete_lines()`, search, shell commands.

## LSP Integration

- Format-on-write (rustfmt, prettier, gofmt, etc.)
- Diagnostics after every change
- 40+ languages out of the box
- Hover docs, symbol search

## Browser Tool

Headless browser with 14 stealth scripts:

- Navigation, clicks, screenshots
- Accessibility snapshots
- Reader mode for content extraction

## Task Tool (Subagents)

6 built-in agents for parallel work: explore, plan, designer, reviewer, task, quick_task.

## Web Search & Fetch

Multiple providers: Exa, Jina, Perplexity, Anthropic, Gemini, and others.

## Full Tool List

`ask`, `bash`, `python`, `calc`, `ssh`, `edit`, `find`, `grep`, `lsp`, `notebook`, `read`, `browser`, `task`, `todo_write`, `fetch`, `web_search`, `write`

## Summary

OMP provides a rich toolkit for any task — from commits to browser automation.
