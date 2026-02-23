---
title: "NTM: Your Agent Orchestrator"
weight: 7
bookToc: true
---

# NTM: Your Agent Orchestrator

## What Is NTM?

**NTM** (Neuro-Tmux Manager) is a tool that manages your AI agents like a conductor manages an orchestra. Instead of manually opening terminals and typing commands for each agent, NTM does it all from one place.

### Why You Need It

Without NTM:
- Open terminal → start Claude → give task → wait → switch terminal → start Codex → give task → wait...

With NTM:
- Open NTM → assign tasks to 3 agents at once → they all work in parallel

### Starting NTM

```bash
ntm
```

This opens a **TUI** (Text User Interface) — a visual program that runs in your terminal.

### Key Concepts

- **Slots** — numbered positions where agents run (like parking spots)
- **Prompts** — instructions you send to agents
- **Broadcast** — send the same instruction to all agents at once

### Basic Workflow

1. Open NTM: `ntm`
2. Spawn agents into slots
3. Send prompts (instructions) to one or all agents
4. Watch them work in parallel
5. Review their output

### The Command Palette

Press the shortcut key to open the command palette — a quick menu of all available actions. This is the fastest way to control NTM.

### When to Use NTM

- Working on a project that benefits from multiple perspectives
- Need to compare solutions from different AI agents
- Want to parallelize work (frontend + backend + tests simultaneously)

### Key Takeaway

NTM lets you manage multiple AI agents from a single interface. Spawn agents, broadcast prompts, and watch them work in parallel. It's your mission control.
