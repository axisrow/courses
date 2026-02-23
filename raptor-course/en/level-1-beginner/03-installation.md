---
title: "Installing RAPTOR"
weight: 3
bookToc: true
---

## Installing RAPTOR

### Prerequisites

Before you begin, you need:

- A computer running Linux or macOS (Windows works with WSL)
- **Claude Code** installed (download from https://claude.ai/download)
- An **Anthropic API key** for AI-powered analysis
- **Git** for downloading the code

### Step-by-Step Installation

#### Option 1: Manual Install

```bash
# Download RAPTOR
git clone https://github.com/gadievron/raptor.git
cd raptor

# Start Claude Code
claude

# Inside Claude, install dependencies
"Install dependencies from requirements.txt"
"Install semgrep"
"Set my ANTHROPIC_API_KEY to YOUR_KEY_HERE"
```

#### Option 2: DevContainer (Recommended for Beginners)

The DevContainer comes with everything pre-installed. Open the RAPTOR folder in VS Code and select **Dev Container: Open Folder in Container**.

Or build it manually:

```bash
docker build -f .devcontainer/Dockerfile -t raptor-devcontainer:latest .
```

### What Gets Installed?

- **Semgrep** — static analysis engine
- **CodeQL** — semantic code analysis by GitHub
- **AFL++** — fuzzing tool
- **rr debugger** — record-replay debugging

### Key Takeaway

The easiest way to start is with the DevContainer. It handles all dependencies for you. If you prefer manual setup, follow the steps above and let Claude Code guide you.
