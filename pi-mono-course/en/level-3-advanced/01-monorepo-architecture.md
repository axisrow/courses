---
title: "Monorepo Architecture"
weight: 1
bookToc: true
---

# Monorepo Architecture

## Introduction

Pi Mono is organized as a monorepo — all packages live in one Git repository managed via npm workspaces.

## Project Structure

```
pi-mono/
├── packages/
│   ├── ai/              # Unified LLM API
│   ├── agent/           # Agent runtime
│   ├── coding-agent/    # CLI coding assistant
│   ├── mom/             # Slack bot
│   ├── tui/             # Terminal UI
│   ├── web-ui/          # Web components
│   └── pods/            # GPU pod management
├── package.json         # Root workspace config
├── AGENTS.md            # Project rules
├── CONTRIBUTING.md      # Contribution guide
└── test.sh              # Test runner
```

## Package Dependencies

```
coding-agent → agent → ai
                ↓
mom ──────────→ agent → ai
                        ↑
web-ui ─────────────────┘
tui (independent)
pods (independent)
```

## Development Commands

```bash
npm install          # Install all dependencies
npm run build        # Build all packages
npm run check        # Lint, format, type check
./test.sh            # Run tests
```

## Important

`npm run check` requires `npm run build` first, as web-ui uses compiled `.d.ts` files from dependencies.

## Summary

- Pi Mono is a monorepo with npm workspaces
- 7 packages with clear dependencies
- Unified build and test system
