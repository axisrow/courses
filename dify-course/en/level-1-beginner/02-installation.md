---
title: "Installation & Setup"
weight: 2
bookToc: true
---

# Installation & Setup

## Option 1: Dify Cloud

The fastest way to start. Go to [cloud.dify.ai](https://cloud.dify.ai), create an account, and you're ready.

## Option 2: Docker (Self-hosted)

### Prerequisites

- Docker and Docker Compose installed
- At least 4 GB RAM

### Steps

```bash
# Clone the repository
git clone https://github.com/langgenius/dify.git
cd dify/docker

# Copy the environment file
cp .env.example .env

# Start Dify
docker compose up -d
```

Dify will be available at `http://localhost/install`.

### First-time Setup

1. Open `http://localhost/install` in your browser
2. Create an admin account (email + password)
3. You'll land on the dashboard

## Adding a Model Provider

Before building apps, connect at least one LLM:

1. Go to **Settings → Model Providers**
2. Click **Add** next to your provider (e.g., OpenAI)
3. Paste your API key
4. Click **Save**

## Verify It Works

Go to the **Studio** page and click **Create App**. If you see the app creation dialog, everything is set up correctly.

## Next Step

Time to build your first AI app!
