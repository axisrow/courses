---
title: "Coding Agent CLI"
weight: 3
bookToc: true
---

# Coding Agent CLI

## Introduction

Pi Coding Agent is an interactive AI assistant that works right in your terminal. It can read and edit files, run commands, and help you write code.

## Key Features

- **Read files** — the agent can see file contents in your project
- **Edit files** — can create and modify files
- **Bash commands** — executes terminal commands
- **Context awareness** — understands your project structure

## Starting Pi

```bash
pi
```

This launches interactive mode. You'll see an editor for typing messages.

## Modes

Pi works in four modes:

1. **Interactive** — terminal dialog (default)
2. **Print/JSON** — output to stdout
3. **RPC** — for integration with other programs
4. **SDK** — embedding in your own apps

## Default Tools

The agent comes with 4 built-in tools:

- `read` — read files
- `write` — write files
- `edit` — edit files
- `bash` — execute commands

## Usage Example

```
> Create a file hello.py with a Hello World program

The agent will create the file and show the result.
```

## Summary

- Pi Coding Agent is a terminal AI assistant
- Works in 4 modes
- Has 4 basic tools for files and commands
