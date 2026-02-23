---
title: "Slack Bot (Mom)"
weight: 5
bookToc: true
---

# Slack Bot (Mom)

## Introduction

**Mom** (Master Of Mischief) is an LLM-powered Slack bot that can execute commands, work with files, and automate workflows. Mom installs her own tools and manages her environment autonomously.

## Features

- **Self-managing** — installs tools and configures her environment
- **Bash access** — executes any commands
- **Docker sandbox** — secure isolation
- **Working memory** — remembers context across sessions
- **CLI tool creation** — writes custom scripts for recurring tasks

## Installation

```bash
npm install @mariozechner/pi-mom
```

## Slack Setup

1. Create an app at https://api.slack.com/apps
2. Enable **Socket Mode**
3. Add Bot Token Scopes: `chat:write`, `channels:history`, `im:history`, etc.
4. Subscribe to events: `app_mention`, `message.im`
5. Install the app to your workspace

## Quick Start

```bash
export MOM_SLACK_APP_TOKEN=xapp-...
export MOM_SLACK_BOT_TOKEN=xoxb-...
export ANTHROPIC_API_KEY=sk-ant-...

# Docker sandbox (recommended)
docker run -d --name mom-sandbox -v $(pwd)/data:/workspace alpine:latest tail -f /dev/null

# Run
mom --sandbox=docker:mom-sandbox ./data
```

## Summary

- Mom is a self-managing Slack bot powered by Pi
- Runs in a Docker sandbox for security
- Creates her own tools for your tasks
