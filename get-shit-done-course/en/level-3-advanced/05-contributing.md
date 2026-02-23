---
title: "Contributing to GSD"
level: 3
lesson: 5
language: en
tags: [gsd, contributing, open-source]
---

# Contributing to GSD

## Introduction

GSD is an open-source project under the MIT license. You can make changes, fix bugs, and add features.

## Instructions

### Getting Started

```bash
git clone https://github.com/glittercowboy/get-shit-done.git
cd get-shit-done
node bin/install.js --claude --local
```

This installs GSD locally for testing changes.

### Project Structure

```
get-shit-done/
├── bin/
│   └── install.js          # Installer
├── prompts/
│   └── claude/
│       └── commands/gsd/    # Slash commands
├── docs/
│   └── USER-GUIDE.md       # Documentation
└── README.md
```

### What You Can Contribute

- **Commands** — new slash commands or improvements to existing ones
- **Documentation** — fixes, translations, examples
- **Bug fixes** — fixing issues
- **Runtimes** — supporting new AI agents
- **Tests** — improving coverage

### Process

1. Fork the repository
2. Create a branch: `git checkout -b feature/my-feature`
3. Make changes
4. Test locally via `node bin/install.js --claude --local`
5. Create a Pull Request

### Community

- [Discord](https://discord.gg/5JJgD5svVS) — questions and discussions
- [GitHub Issues](https://github.com/glittercowboy/get-shit-done/issues) — bugs and proposals
- [Twitter/X](https://x.com/gsd_foundation) — news

## Examples

```bash
# Testing command changes
cd get-shit-done
# Edit prompts/claude/commands/gsd/some-command.md
node bin/install.js --claude --local
# Open Claude Code and test /gsd:some-command
```

## Summary

- GSD is open-source (MIT)
- Clone and install locally for development
- Contribute commands, docs, fixes
- Community on Discord
- PRs through standard GitHub process
