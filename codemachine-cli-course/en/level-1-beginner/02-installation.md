---
title: "Installing CodeMachine"
weight: 2
bookToc: true
---

# Installing CodeMachine

## What You Need

Before installing CodeMachine, make sure you have:

1. **Node.js** (version 18 or higher) — a program that runs JavaScript on your computer
2. **A terminal** — the text-based interface on your computer (Terminal on Mac, Command Prompt or PowerShell on Windows)
3. **An AI engine** — at least one of: Claude Code, Codex CLI, or Cursor

> **Don't have Node.js?** Visit [nodejs.org](https://nodejs.org) and download the latest version. Installation is straightforward — just follow the on-screen instructions.

## Step-by-Step Installation

Open your terminal and type:

```bash
npm i -g codemachine
```

This command installs CodeMachine globally on your computer. The `-g` flag means "global" — you can use it from any folder.

## Verify the Installation

After installation, check that everything works:

```bash
codemachine --version
```

You should see a version number (like `0.8.0`). If you see an error, try closing and reopening your terminal.

## The Short Command

CodeMachine has a short alias. Instead of typing `codemachine`, you can type:

```bash
cm
```

Both commands do exactly the same thing.

## Important Rule

CodeMachine must run inside a **project folder**, not your home directory. Always navigate to your project first:

```bash
cd ~/my-project
codemachine
```

Or specify the directory:

```bash
codemachine --dir ~/my-project
```

## Summary

- Install with `npm i -g codemachine`
- Verify with `codemachine --version`
- Use `cm` as a shortcut
- Always run inside a project folder

> **Next lesson:** We'll create your first project and explore the CodeMachine interface.
