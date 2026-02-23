---
title: "Git Strategy and Repo Management"
weight: 13
bookToc: true
---

# Git Strategy and Repo Management

## Why Git Matters in Agentic Coding

When multiple AI agents write code simultaneously, you need solid version control. Git is your safety net and coordination tool.

### The Basic Git Model

Think of Git like a save system in a video game:
- **Commit** = saving your game
- **Branch** = creating an alternate timeline
- **Merge** = combining two timelines
- **Push** = uploading your saves to the cloud

### ACFS Git Workflow

```
main branch (production-ready code)
    ├── feature/agent-claude-backend
    ├── feature/agent-codex-frontend
    └── feature/agent-gemini-tests
```

Each agent works on its own branch. This prevents conflicts.

### RU — Repository Utility

RU helps manage multiple repositories:

```bash
# Sync all your repos
ru sync

# AI-driven commit messages across dirty repos
ru commit
```

When you have 10+ projects, RU saves enormous time by automating routine git operations.

### Best Practices

1. **One branch per agent per task** — prevents conflicts
2. **Commit often** — small, frequent saves are better than rare, huge ones
3. **Use Agent Mail file reservations** — prevent two agents from editing the same file
4. **Scan before merging** — run UBS on each branch before merging to main
5. **Review agent PRs** — always review what agents wrote before merging

### CAAM — Cloud Auth Account Manager

When working across multiple GitHub accounts or cloud services:

```bash
# Switch between git identities
caam switch work
caam switch personal
```

This prevents accidentally pushing code to the wrong repository.

### Key Takeaway

Use separate branches for each agent's work. RU automates repo management across many projects. CAAM handles identity switching. Always review agent code before merging to main.
