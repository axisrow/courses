---
title: "Troubleshooting and Best Practices"
weight: 15
bookToc: true
---

# Troubleshooting and Best Practices

## Common Issues and Solutions

### "Command not found"

If a command doesn't work after installation:

```bash
# Reload your shell configuration
source ~/.zshrc

# Or start a new shell
exec zsh
```

### "Agent won't start"

API keys might be missing:
- Claude: needs `ANTHROPIC_API_KEY`
- Codex: needs `OPENAI_API_KEY`
- Gemini: needs `GOOGLE_API_KEY`

```bash
# Check if keys are set
echo $ANTHROPIC_API_KEY
echo $OPENAI_API_KEY
echo $GOOGLE_API_KEY
```

### "Installation failed midway"

Just run the installer again — it's idempotent:

```bash
curl -fsSL "https://raw.githubusercontent.com/Dicklesworthstone/agentic_coding_flywheel_setup/main/install.sh" | bash -s -- --yes --mode vibe
```

### "Tmux session disappeared"

```bash
# List all sessions
tmux ls

# If empty, sessions were lost (server reboot?)
# Just create new ones — your code is still in the filesystem
```

### Running Diagnostics

```bash
# Full system health check
acfs doctor

# Check specific tool
which claude  # Shows path if installed
claude --version  # Shows version
```

## Best Practices

### Daily Workflow
1. SSH into your VPS
2. Reattach to tmux sessions: `tmux attach`
3. Use NTM to manage agents
4. Run `acfs doctor` weekly

### Project Workflow
1. Create a new branch for each feature
2. Assign agents via NTM
3. Use Agent Mail for coordination
4. Scan with UBS before merging
5. Run `cm reflect` after completing the project

### Safety Habits
1. Keep VPS snapshots (backups) before major changes
2. Never run ACFS vibe mode on production servers
3. Review agent-written code before deploying
4. Use DCG and SLB — don't disable them
5. Commit frequently — it's your undo button

### When to Start Over

Sometimes the fastest fix is a fresh start:
1. Create a new VPS
2. Run ACFS installer
3. Clone your repos
4. You're back in business in 30 minutes

That's the beauty of the ACFS approach — your code lives in Git, your VPS is disposable.

### Key Takeaway

Most issues are solved by reloading your shell or re-running the installer. Run `acfs doctor` for diagnostics. Keep your code in Git so your VPS stays disposable. Review agent work before deploying.
