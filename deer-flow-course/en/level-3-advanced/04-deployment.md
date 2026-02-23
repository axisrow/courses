---
title: "Deploying DeerFlow"
weight: 4
bookToc: true
---

# Deploying DeerFlow

## Introduction

In this lesson we'll cover how to deploy DeerFlow in production — from Docker Compose to Kubernetes.

## Docker Compose (Recommended)

### Deployment Architecture

```
Docker Compose
  ├─ nginx (port 2026)      ← Reverse proxy
  ├─ web (port 3000)        ← Frontend
  ├─ api (port 8001)        ← Gateway API
  └─ langgraph (port 2024)  ← LangGraph Server
```

### Steps

#### 1. Prepare the server

```bash
sudo apt update
sudo apt install -y docker.io docker-compose-v2 git
sudo systemctl enable docker
```

#### 2. Clone and configure

```bash
git clone https://github.com/bytedance/deer-flow.git
cd deer-flow
make config
```

#### 3. Set environment variables

```bash
# .env
OPENAI_API_KEY=sk-your-key
```

#### 4. Configure the sandbox

For production, use the Docker sandbox:

```yaml
sandbox:
  use: src.community.aio_sandbox:AioSandboxProvider
```

#### 5. Initialize and start

```bash
make docker-init    # First time
make docker-start   # Start
```

#### 6. Verify

```bash
curl http://localhost:2026/api/health
# Expected: {"status": "ok"}
```

## Kubernetes

For scalable deployments with isolated sandbox pods:

```yaml
sandbox:
  use: src.community.aio_sandbox:AioSandboxProvider
  provisioner_url: http://provisioner:8002
```

## Security Checklist

- [ ] Use Docker sandbox (not local)
- [ ] API keys only via environment variables
- [ ] HTTPS for external access
- [ ] Authentication before proxy
- [ ] Limit sandbox network access
- [ ] Regularly update Docker images
- [ ] Monitor API key usage

## Monitoring

```bash
make docker-logs              # All services
docker compose logs -f api    # Specific service
```

## Summary

- Docker Compose is the recommended deployment method
- Use Docker sandbox for production
- Set up HTTPS and authentication for external access
- API keys — only via environment variables
- Kubernetes for scalable deployments
