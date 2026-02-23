---
title: "Installation"
weight: 2
bookToc: true
---

# Installing DeerFlow

## Introduction

In this lesson, we'll install DeerFlow on your computer step by step. There are two methods: via **Docker** (recommended) and manually. Docker is a program that creates isolated containers for applications — like "boxes" with everything needed inside.

## What You'll Need

- A computer with Windows, macOS, or Linux
- Internet connection
- An API key from an AI provider (OpenAI, Anthropic, DeepSeek, etc.)

> **API key** — a unique password that lets your application communicate with an AI service. You can get one from the provider's website (e.g., platform.openai.com).

## Method 1: Docker Installation (Recommended)

### Step 1: Install Docker

1. Go to [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. Download Docker Desktop for your OS
3. Install and launch Docker Desktop

### Step 2: Install pnpm

**pnpm** is a JavaScript package manager (like npm, but faster).

```bash
npm install -g pnpm
# Or via script
curl -fsSL https://get.pnpm.io/install.sh | sh -
```

### Step 3: Clone the repository

```bash
git clone https://github.com/bytedance/deer-flow.git
cd deer-flow
```

### Step 4: Create configuration files

```bash
make config
```

### Step 5: Set up API keys

Edit the `.env` file:

```bash
OPENAI_API_KEY=sk-your-key-here
```

### Step 6: Launch DeerFlow

```bash
make docker-init    # First time only
make docker-start   # Start all services
```

### Step 7: Open in browser

Go to: **http://localhost:2026**

🎉 Done! DeerFlow is running.

## Method 2: Local Installation

### Prerequisites

- **Node.js 22+** ([nodejs.org](https://nodejs.org))
- **pnpm**
- **Python 3.12+** ([python.org](https://python.org))
- **uv** — Python package manager (`pip install uv`)
- **nginx** — web server

### Steps

```bash
make check          # Verify dependencies
git clone https://github.com/bytedance/deer-flow.git
cd deer-flow
make config
# Edit .env with your API keys
make dev
```

Open **http://localhost:2026** in your browser.

## Service Management

| Command | Description |
|---------|-------------|
| `make docker-start` | Start all services (Docker) |
| `make docker-stop` | Stop all services |
| `make docker-restart` | Restart services |
| `make docker-logs` | Show logs |
| `make dev` | Start locally |
| `make stop` | Stop local services |

## Troubleshooting

- **"Port 2026 is already in use"** — Stop the other program or change the port
- **"Docker daemon is not running"** — Launch Docker Desktop
- **"API key is invalid"** — Check your key in `.env`

## Summary

- DeerFlow can be installed via Docker (easier) or locally
- You need an API key from an AI provider
- Web interface is available at http://localhost:2026
- Use `make` commands for management

In the next lesson, we'll make our first request to DeerFlow.
