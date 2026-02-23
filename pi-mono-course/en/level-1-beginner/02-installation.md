---
title: "Installing Pi Mono"
weight: 2
bookToc: true
---

# Installing Pi Mono

## Introduction

In this lesson, we'll install Pi Mono and set up the working environment.

## Requirements

- **Node.js** version 18 or higher
- **npm** (installed with Node.js)
- A terminal (command line)

## Step-by-Step Installation

### Step 1: Install Node.js

Download Node.js from [nodejs.org](https://nodejs.org) and install it. Verify:

```bash
node --version
npm --version
```

### Step 2: Install the coding agent

```bash
npm install -g @mariozechner/pi-coding-agent
```

### Step 3: Set up your API key

You need a key to work with AI models. For Anthropic:

```bash
export ANTHROPIC_API_KEY=sk-ant-your-key
```

Or use built-in authentication:

```bash
pi
/login
```

### Step 4: Verify installation

```bash
pi --help
```

## Summary

- Installed Node.js and npm
- Installed Pi coding agent globally
- Configured an API key for an LLM provider
