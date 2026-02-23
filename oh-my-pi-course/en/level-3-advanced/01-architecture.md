---
title: "Architecture (TypeScript + Rust + Bun)"
level: 3
lesson: 1
lang: en
tags: [architecture, typescript, rust, bun, monorepo]
---

# Oh My Pi Architecture

## Introduction

OMP is a monorepo combining TypeScript, Rust, and Bun for maximum performance.

## Technology Stack

- **TypeScript** — core logic, TUI, agent, SDK
- **Rust** — native modules via N-API (~7,500 lines)
- **Bun** — runtime instead of Node.js (faster, native TypeScript)

## Monorepo Packages

| Package | Description |
|---------|-------------|
| `@oh-my-pi/pi-ai` | Multi-provider LLM client |
| `@oh-my-pi/pi-agent-core` | Agent runtime with tool calling |
| `@oh-my-pi/pi-coding-agent` | Coding agent CLI and SDK |
| `@oh-my-pi/pi-tui` | Terminal UI library |
| `@oh-my-pi/pi-natives` | N-API bindings (Rust) |
| `@oh-my-pi/omp-stats` | Stats dashboard |
| `@oh-my-pi/pi-utils` | Utilities |

## Native Engine (Rust)

| Module | Lines | What it does | Powered by |
|--------|-------|-------------|------------|
| grep | ~1,300 | Regex search over files | ripgrep internals |
| shell | ~1,025 | Embedded bash execution | brush-shell |
| text | ~1,280 | ANSI-aware text processing | unicode-width |
| keys | ~1,300 | Kitty keyboard parser | phf |
| highlight | ~475 | Syntax highlighting | syntect |
| glob | ~340 | File discovery | ignore, globset |
| task | ~350 | Work scheduler | tokio, napi |
| ps | ~290 | Process management | libc |
| prof | ~250 | Profiler | inferno |
| image | ~150 | Image processing | image |
| clipboard | ~95 | Clipboard access | arboard |
| html | ~50 | HTML → Markdown | html-to-markdown-rs |

Platforms: linux-x64, linux-arm64, darwin-x64, darwin-arm64, win32-x64.

## Summary

OMP's architecture combines TypeScript convenience with Rust performance, using Bun as a fast runtime.
