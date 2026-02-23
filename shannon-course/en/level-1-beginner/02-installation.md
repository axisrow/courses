---
title: "Installation"
weight: 2
bookToc: true
---

# Installation

## Introduction

In this lesson, we'll install everything needed to run Shannon on your computer.

## Prerequisites

1. **Docker** — containerization system (Shannon runs in containers)
2. **Anthropic API key** — Shannon uses Claude AI for analysis

## Step 1: Install Docker

### macOS
Download and install [Docker Desktop](https://docs.docker.com/get-docker/). Works out of the box.

### Windows
WSL2 is recommended:

```powershell
wsl --install
wsl --set-default-version 2
wsl --install Ubuntu-24.04
```

Then install Docker Desktop and enable "Use the WSL 2 based engine" in settings.

### Linux
Install Docker via the [official guide](https://docs.docker.com/get-docker/). You may need `sudo`.

## Step 2: Get an API Key

1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Sign up or log in
3. Create an API key
4. Save it — you'll need it next

## Step 3: Clone Shannon

```bash
git clone https://github.com/KeygraphHQ/shannon.git
cd shannon
```

## Step 4: Configure Credentials

Create a `.env` file in the Shannon directory:

```bash
cat > .env << 'EOF'
ANTHROPIC_API_KEY=your-key-here
CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
EOF
```

Or export environment variables:

```bash
export ANTHROPIC_API_KEY="your-key-here"
export CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
```

## Step 5: Verify

Make sure Docker is running:

```bash
docker --version
```

If you see a Docker version — you're all set!

## Summary

- You installed Docker
- Got an Anthropic API key
- Cloned the Shannon repository
- Configured credentials

In the next lesson, we'll launch Shannon for the first time.
