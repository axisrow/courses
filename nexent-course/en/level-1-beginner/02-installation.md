---
title: "Installation & First Launch"
weight: 2
bookToc: true
---

# Installation & First Launch

## What You Need

Before installing Nexent, make sure your computer meets these minimum requirements:

| Resource | Minimum |
|----------|---------|
| **CPU** | 2 cores |
| **RAM** | 6 GB |
| **Software** | Docker and Docker Compose installed |

> **What is Docker?** Docker is a tool that runs applications inside isolated containers. If you don't have it yet, visit [docker.com](https://www.docker.com/) and follow the installation guide for your operating system.

## Step-by-Step Installation

### 1. Download Nexent

Open your terminal (or command prompt) and run:

```bash
git clone https://github.com/ModelEngine-Group/nexent.git
```

This downloads the entire Nexent project to your computer.

### 2. Go to the Docker Folder

```bash
cd nexent/docker
```

### 3. Create Your Configuration File

```bash
cp .env.example .env
```

Open the `.env` file in any text editor. For a basic setup, you only need to fill in the voice service credentials (or leave them blank if you don't need voice features).

### 4. Launch Nexent

```bash
bash deploy.sh
```

The script will download and start all necessary containers. This may take a few minutes on the first run.

### 5. Open the Browser

Go to **http://localhost:3000**. You will see the Nexent setup wizard.

## The Setup Wizard

When you first open Nexent, a wizard will guide you through:

1. **Choosing a language** — English or Chinese.
2. **Connecting an AI model** — You'll need an API key from a model provider (e.g., OpenAI, SiliconFlow, or others).
3. **Basic preferences** — Name your workspace and set defaults.

## Stopping and Restarting

To stop Nexent:

```bash
cd nexent/docker
docker compose down
```

To start it again:

```bash
bash deploy.sh
```

Your data is preserved between restarts.

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Port 3000 is busy | Stop the other application using that port, or edit `docker-compose.yml` to change the port |
| Not enough memory | Close other programs or increase Docker's memory limit in Docker Desktop settings |
| Containers fail to start | Run `docker compose logs` and look for error messages |

You're now ready for your first conversation!
