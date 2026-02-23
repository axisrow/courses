---
title: "Installing Codex"
weight: 2
bookToc: true
---

# Installing Codex

## Introduction

Codex is an AI agent from OpenAI that runs in the command line (CLI). It uses Skills to perform tasks. In this lesson we will install Codex on your computer.

## Requirements

- A computer with macOS, Windows, or Linux
- Node.js installed (version 18 or newer)
- An OpenAI account with an API key

## Step-by-Step Installation

### Step 1: Check Node.js

Open a terminal and type:

```bash
node --version
```

If the version is below 18 or Node.js is not installed, download it from [nodejs.org](https://nodejs.org).

### Step 2: Install Codex

```bash
npm install -g @openai/codex
```

### Step 3: Set Up Your API Key

```bash
export OPENAI_API_KEY="your-key"
```

To persist the key across sessions, add this line to `~/.bashrc` or `~/.zshrc`.

### Step 4: Verify Installation

```bash
codex --help
```

You should see a list of available commands.

## Where Skills Are Stored

After installation Codex creates a home directory:

```
~/.codex/
└── skills/     — skills are installed here
```

System skills (`.system`) are built into Codex and available immediately.

## Summary

- Codex is installed via npm
- An OpenAI API key is required
- Skills are stored in `~/.codex/skills/`
- System skills are available right after installation
