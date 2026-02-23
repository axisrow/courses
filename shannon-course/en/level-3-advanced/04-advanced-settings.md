---
title: "Advanced Settings"
weight: 4
bookToc: true
---

# Advanced Settings

## Introduction

Advanced Shannon capabilities: alternative providers, workspace management, and optimization.

## Router Mode: Alternative AI Providers

```bash
# In .env
OPENAI_API_KEY=sk-...
ROUTER_DEFAULT=openai,gpt-5.2

# Or via OpenRouter
OPENROUTER_API_KEY=sk-or-...
ROUTER_DEFAULT=openrouter,google/gemini-3-flash-preview
```

```bash
./shannon start URL=https://app.com REPO=app ROUTER=true
```

> ⚠️ Experimental. Quality depends on the model. Some may fail early phases.

## Workspace Management

```bash
./shannon workspaces                    # List all
./shannon start ... WORKSPACE=q1-audit  # Named workspace
# Resume interrupted test by reusing the same workspace name
```

Each agent checkpoints via git commits, so resumption starts from a clean state.

## Temporal Web UI

Open `http://localhost:8233` for detailed monitoring: workflow status, agent progress, timing, errors.

## Cost Optimization

- Typical run: ~$50 on Claude 4.5 Sonnet
- Router Mode with cheaper models trades quality for cost
- Workspaces save money: no need to restart everything on failure

## Windows Tips

- Use WSL2 for best compatibility
- Add Shannon directory to Windows Defender exclusions (PoC code triggers false positives)

## Summary

- Router Mode enables experimenting with other AI models
- Workspaces organize and resume tests
- Temporal UI provides detailed monitoring
- Model choice affects both cost and quality
