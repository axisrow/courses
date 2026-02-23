---
title: "Installation and Setup"
weight: 3
bookToc: true
---

# Installation and Setup

## Prerequisites

Before you begin, make sure you have:

- A computer running **Windows, macOS, or Linux**.
- **Docker** installed (Docker Desktop is the easiest option).
- **Node.js** (version 18 or higher) for the client.
- **Python 3.11+** for the server.
- A **Git** client to clone the repository.

## Step 1 — Clone the Repository

```bash
git clone https://github.com/existence-master/Sentient.git
cd Sentient
```

## Step 2 — Configure Environment Variables

Both the client and server need `.env` files. Templates are provided:

```bash
# Server
cp src/server/.env.template src/server/.env

# Client
cp src/client/.env.template src/client/.env
```

Open each `.env` file and fill in the required values (API keys, database URLs, etc.). The comments in each template explain what each variable does.

## Step 3 — Start the Databases

Sentient ships Docker Compose files for its databases:

```bash
# PostgreSQL with pgvector
docker compose -f start_pgvector.yaml up -d

# Redis
docker compose -f start_redis.yaml up -d  # or use the PowerShell script

# ChromaDB
docker compose -f start_chroma.yaml up -d

# LiteLLM proxy
docker compose -f start_litellm.yaml up -d
```

## Step 4 — Start the Server

```bash
cd src/server
pip install -r requirements.txt
python -m uvicorn main.app:app --reload
```

## Step 5 — Start the Client

```bash
cd src/client
npm install
npm run dev
```

Open your browser and navigate to `http://localhost:3000`. You should see the Sentient interface.

## Self-Host with Docker Compose

For a fully containerized setup, use the provided self-host file:

```bash
docker compose -f src/docker-compose.selfhost.yml up -d
```

This starts everything — client, server, databases — in one command.

## Summary

You now have Sentient running locally. In the next lesson, you'll learn how to have your first conversation and explore the interface.
