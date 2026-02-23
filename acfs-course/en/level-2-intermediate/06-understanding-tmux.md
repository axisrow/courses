---
title: "Mastering Tmux for Persistent Sessions"
weight: 6
bookToc: true
---

# Mastering Tmux for Persistent Sessions

## Why Tmux Matters

When you close your laptop or your WiFi drops, a normal SSH session dies — and everything you were running stops. **Tmux** solves this completely.

### The Basics

Think of tmux like having multiple desktops on your VPS:

- **Sessions** — like separate workspaces
- **Windows** — like tabs in a browser
- **Panes** — like splitting your screen

### Essential Commands

```bash
# Create a new named session
tmux new -s mywork

# Detach (leave session running in background)
# Press: Ctrl+B, then D

# List all sessions
tmux ls

# Reconnect to a session
tmux attach -t mywork
```

### The ACFS Tmux Setup

ACFS pre-configures tmux with useful settings:
- Mouse support enabled (you can click on panes)
- Better keyboard shortcuts
- A status bar showing useful info

### Splitting Your Screen

```bash
# Split horizontally (top/bottom)
Ctrl+B, then "

# Split vertically (left/right)
Ctrl+B, then %

# Switch between panes
Ctrl+B, then arrow keys
```

### Real-World Workflow

```
Session "coding"          Session "monitoring"
├── Window 1: Agent 1     ├── Window 1: Logs
├── Window 2: Agent 2     └── Window 2: System stats
└── Window 3: Testing
```

You can have one agent writing code in one session, another reviewing it in a second session, and switch between them instantly.

### Key Takeaway

Tmux keeps your work alive when you disconnect. Learn `tmux new -s NAME`, `Ctrl+B D` to detach, and `tmux attach -t NAME` to reconnect. It's your safety net.
