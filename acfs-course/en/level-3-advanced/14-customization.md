---
title: "Customizing Your ACFS Environment"
weight: 14
bookToc: true
---

# Customizing Your ACFS Environment

## Making It Yours

ACFS comes with sensible defaults, but you can customize everything. Your customizations survive updates.

### Key Configuration Files

| File | What It Controls |
|------|-----------------|
| `~/.acfs/` | Main ACFS configuration directory |
| `~/.zshrc` | Shell behavior and aliases |
| `~/.tmux.conf` | Tmux layout and shortcuts |

### Environment Variables

```bash
# Change ACFS home directory
export ACFS_HOME=~/.acfs

# Set log directory
export ACFS_LOG_DIR=/var/log/acfs

# Configure target user
export TARGET_USER=ubuntu
```

### Installer Modes

ACFS supports different installation modes:

- **`--mode vibe`** — Maximum velocity. Dangerous flags enabled. Great for throwaway VPS.
- Default mode — More conservative. Asks for confirmations.

### Custom Agent Configurations

Each agent can be configured with ACFS-provided settings:

```bash
# Claude Code settings are in:
~/.acfs/claude/settings.json
```

### The Wizard Website

For a visual setup experience, visit [agent-flywheel.com](https://agent-flywheel.com). It provides a 13-step guided wizard that walks you through everything with a visual interface.

### Security Considerations

**Vibe mode** enables flags like:
- `--dangerously-skip-permissions` (Claude)
- `--dangerously-bypass-approvals-and-sandbox` (Codex)
- `--yolo` (Gemini)

This is **intentionally insecure for speed**. Only use on:
- ✅ Throwaway VPS
- ✅ Personal experiments
- ❌ Never on production servers
- ❌ Never on shared infrastructure

### Key Takeaway

ACFS is highly customizable through environment variables, config files, and installer modes. Use vibe mode for maximum speed on throwaway servers, but never on production. Visit agent-flywheel.com for a guided visual setup.
