---
title: "Contributing"
level: 3
lesson: 5
lang: en
tags: [contributing, open source, PR, development]
---

# Contributing to Oh My Pi

## Introduction

OMP is an open source project under the MIT license. Here's how to contribute.

## Getting Started

1. Fork the repository on GitHub
2. Clone your fork
3. Create a branch for your changes

```bash
git clone https://github.com/YOUR_USERNAME/oh-my-pi.git
cd oh-my-pi
git checkout -b feature/my-improvement
bun install
```

## Types of Contributions

### Bug Reports
- Use GitHub Issues
- Include OMP version, OS, terminal
- Attach logs from `~/.omp/logs/`

### New Features
- Discuss the idea in an Issue or on Discord
- Follow existing code patterns

### New Providers
- Add configuration in `packages/ai/`

### Custom Tools
- Create in `packages/coding-agent/src/tools/`

### Themes
- Add a JSON file to `packages/coding-agent/themes/`

### Documentation
- `docs/` folder

## Pull Request Process

1. Make sure code builds: `bun run build`
2. Run tests
3. Use conventional commits
4. Describe changes in the PR

```bash
# Use OMP for commits!
omp commit --push
```

## Resources

- [DEVELOPMENT.md](https://github.com/can1357/oh-my-pi/blob/main/packages/coding-agent/DEVELOPMENT.md)
- [Discord](https://discord.gg/4NMW9cdXZa)
- [CHANGELOG.md](https://github.com/can1357/oh-my-pi/blob/main/packages/coding-agent/CHANGELOG.md)

## License

MIT. Copyright (c) 2025 Mario Zechner, 2025-2026 Can Bölük.

## Summary

Contributions to OMP are welcome — from bug reports to new features. Use GitHub Issues and PRs with conventional commits.
