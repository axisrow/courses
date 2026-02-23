---
title: "Running the ACFS Installer"
weight: 4
bookToc: true
---

# Running the ACFS Installer

## The Magic Command

Once you're connected to your VPS via SSH, run this single command:

```bash
curl -fsSL "https://raw.githubusercontent.com/Dicklesworthstone/agentic_coding_flywheel_setup/main/install.sh" | bash -s -- --yes --mode vibe
```

### What Does This Do?

Let's break it down in plain language:

- `curl` — downloads a file from the internet
- `|` — sends it directly to...
- `bash` — the program that runs commands
- `--yes` — automatically answer "yes" to all questions
- `--mode vibe` — install everything with maximum speed settings

### What Gets Installed (30+ Tools)

The installer sets up:

1. **A beautiful terminal** — colorful, with helpful shortcuts
2. **Programming languages** — Python, JavaScript, Rust, Go
3. **Three AI coding agents** — Claude Code, Codex CLI, Gemini CLI
4. **10 coordination tools** — for managing multiple AI agents
5. **Cloud tools** — for deploying your projects
6. **Developer tools** — for searching, editing, and managing code

### How Long Does It Take?

About **30 minutes**. You can watch it work or go make coffee.

### What If It Fails?

The installer is **idempotent** — a fancy word meaning "you can run it again safely." If your internet drops or something goes wrong, just run the same command again. It picks up where it left off.

### Key Takeaway

One command installs everything. It takes about 30 minutes. If it fails, just run it again — it's designed to be re-run safely.
