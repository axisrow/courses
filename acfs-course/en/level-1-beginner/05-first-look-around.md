---
title: "Your First Look Around"
weight: 5
bookToc: true
---

# Your First Look Around

## Welcome to Your New Workshop

After ACFS finishes installing, you'll see a colorful terminal prompt. Let's explore what you have.

### The Terminal Looks Different Now

Your terminal now uses **Powerlevel10k** — a beautiful theme that shows useful information:
- Which folder you're in
- Whether you're in a Git repository
- How long the last command took

### Try These Commands

```bash
# See what's installed
acfs doctor
```

This checks that everything was installed correctly. Green means good!

```bash
# Start the onboarding tutorial
onboard
```

This opens a built-in tutorial that walks you through the basics.

### Meet Your AI Agents

You have three AI coding assistants. Try saying hello:

```bash
# Claude Code (by Anthropic)
cc "Hello, what can you do?"

# Codex CLI (by OpenAI)
cod "Hello, what can you do?"

# Gemini CLI (by Google)
gmi "Hello, what can you do?"
```

> **Note**: You'll need API keys for each agent. The installer will guide you through setting them up.

### The Tmux Safety Net

Your VPS uses **tmux** — a tool that keeps your work running even if your internet disconnects. Think of it as saving your game automatically.

```bash
# See active tmux sessions
tmux list-sessions
```

### Key Takeaway

After installation, use `acfs doctor` to verify everything works, `onboard` to start learning, and `cc`, `cod`, or `gmi` to talk to your AI agents. Tmux keeps everything running even if you disconnect.
