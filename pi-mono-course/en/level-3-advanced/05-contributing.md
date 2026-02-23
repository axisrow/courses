---
title: "Contributing"
weight: 5
bookToc: true
---

# Contributing

## Introduction

Pi Mono is an open-source project under the MIT license. This lesson explains how to contribute.

## Getting Started

### Step 1: Clone the repository

```bash
git clone https://github.com/badlogic/pi-mono.git
cd pi-mono
```

### Step 2: Install dependencies

```bash
npm install
```

### Step 3: Build the project

```bash
npm run build
```

### Step 4: Run tests

```bash
./test.sh
```

## Project Rules

Study these files:
- **CONTRIBUTING.md** — contribution guide
- **AGENTS.md** — project rules (for humans and agents)

## Workflow

1. Create a feature branch
2. Make your changes
3. Run `npm run check`
4. Run tests
5. Create a Pull Request

## Running Pi from Source

```bash
./pi-test.sh    # Run pi from source code
```

## Test Structure

Tests that depend on LLM API keys are skipped when keys aren't set, allowing basic tests without provider setup.

## Community

- [Discord](https://discord.com/invite/3cU7Bz4UPx) — main communication channel
- GitHub Issues — bugs and suggestions
- Pull Requests — code contributions

## Summary

- Pi Mono is open to contributions
- Follow CONTRIBUTING.md and AGENTS.md
- Use Discord for questions
