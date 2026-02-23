---
title: "Contributing and Roadmap"
weight: 15
bookToc: true
---

# Contributing and Roadmap

## Why Contribute?

Sentient is community-driven and licensed under **GNU AGPL**. Contributing helps make personal AI accessible to everyone. Plus, it's a great way to learn modern AI engineering.

## How to Contribute

1. **Fork** the repository on GitHub.
2. **Clone** your fork locally.
3. Create a **branch** for your feature or fix.
4. Make your changes and write tests.
5. Submit a **Pull Request** using the provided template.
6. Sign the **CLA** (Contributor License Agreement) — see `CLA.md`.

### Development Setup

```bash
# Server (Python)
cd src/server
pip install -r requirements-dev.txt
pytest  # Run tests

# Client (Node.js)
cd src/client
npm install
npm test  # Jest tests
```

## Areas Where Help Is Needed

- **New MCP integrations** — Add support for more apps (Jira, Linear, Spotify, etc.).
- **Improved memory** — Better deduplication, summarization, and relevance ranking.
- **Mobile app** — A React Native or Flutter client.
- **Multi-language UI** — The web interface currently supports English.
- **Performance** — Optimize WebSocket connections and task scheduling.
- **Documentation** — Improve guides, tutorials, and API docs.

## Project Roadmap

The Sentient team's vision progresses in stages:

1. **Current** — A proactive personal assistant with chat, tasks, and integrations.
2. **Near-term** — Fully autonomous agents that can handle complex, multi-day workflows.
3. **Long-term** — Personal super-intelligence — an AI that knows you deeply and acts as a true partner in all areas of life.

## Community

- **GitHub Issues** — Report bugs and request features.
- **Pull Requests** — Contribute code.
- **Email** — existence.sentient@gmail.com for direct contact.

## What You've Learned in This Course

Over 15 lessons across 3 levels, you've gone from "What is Sentient?" to understanding:

- Architecture and installation.
- Chat, voice, and memories.
- Integrations, tasks, and AI models.
- Custom MCP servers, Celery workers, vector databases.
- Security, self-hosting, and contributing.

**You're now ready to use Sentient effectively, customize it for your needs, and even contribute back to the project. Welcome to the community!**

## Summary

Sentient is more than software — it's a movement toward personal AI for everyone. Your contributions, big or small, help shape that future.
