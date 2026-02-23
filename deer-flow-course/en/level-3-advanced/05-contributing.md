---
title: "Contributing to DeerFlow"
weight: 5
bookToc: true
---

# Contributing to DeerFlow

## Introduction

DeerFlow is an open-source project, and community contributions are welcome! In this lesson we'll cover how to set up a development environment, make changes, and submit a Pull Request.

## Development Setup

### Via Docker (Recommended)

```bash
git clone https://github.com/YOUR-USERNAME/deer-flow.git
cd deer-flow
cp config.example.yaml config.yaml
cp extensions_config.example.json extensions_config.json
export OPENAI_API_KEY="your-key"
make docker-init
make docker-start
```

All services start with hot-reload — code changes apply automatically.

### Local Development

```bash
make check    # Node.js 22+, pnpm, uv, nginx
make install
make dev
```

## Code Style

- **Python:** ruff linter/formatter, 240-char line length, Python 3.12+ with type hints
- **Testing:** pytest

```bash
cd backend
make lint      # Check
make format    # Auto-format
pytest tests/  # Run tests
```

## Contribution Process

1. **Create an Issue** — describe what you want to change and why
2. **Create a branch** — `feature/my-feature` or `fix/my-bugfix`
3. **Make changes** — write tests, follow code style, update docs
4. **Verify** — lint, test, ensure the app starts
5. **Commit and push** — `git commit -m "feat: add my new feature"`
6. **Create a Pull Request** — describe what was done and how to test

## What You Can Contribute

- **Skills** — the easiest way; create a `SKILL.md` in `skills/public/`
- **Community tools** — new integrations in `backend/src/community/`
- **Documentation** — fixes, translations, examples
- **Bug fixes** — look for `good first issue` labels on GitHub

## Important Rules

1. Always update documentation after code changes
2. Write tests for new functionality
3. Follow the existing code style
4. Small PRs are better than large ones
5. Your code will be under the MIT license

🎉 Congratulations! You've completed the entire DeerFlow course. You now know how to use, configure, and extend this powerful super-agent platform!
