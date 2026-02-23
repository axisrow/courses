---
title: "Workflow Integration"
level: 3
lesson: 4
language: en
tags: [gsd, integration, workflow, ci-cd]
---

# Workflow Integration

## Introduction

GSD can be integrated into existing workflows: CI/CD, Docker, team collaboration.

## Instructions

### Docker and CI

For containerized environments, use non-interactive install:

```bash
# In Dockerfile
RUN npx get-shit-done-cc --claude --global

# If ~ doesn't expand:
CLAUDE_CONFIG_DIR=/home/user/.claude npx get-shit-done-cc --global
```

### Git Strategies for Teams

For team work, use `phase` or `milestone` strategy:

```
/gsd:settings
> git.branching_strategy = phase
```

Each phase creates a branch, merged at phase completion.

### Committing .planning/ to Git

By default, GSD commits `.planning/`. Benefits:
- Decision history
- Team visibility
- Reproducibility

Disable with `planning.commit_docs = false`.

### Security

Protect sensitive files:

```json
{
  "permissions": {
    "deny": [
      "Read(.env)",
      "Read(.env.*)",
      "Read(**/*.pem)",
      "Read(**/*.key)"
    ]
  }
}
```

### Team Workflow

```
Dev A: /gsd:new-project → creates spec
Team: Review REQUIREMENTS.md and ROADMAP.md
Dev A: /gsd:plan-phase 1 → creates plans
Dev B: /gsd:execute-phase 1 → executes
Dev A: /gsd:verify-work 1 → verifies
```

## Examples

```bash
# CI: install and execute
npx get-shit-done-cc --claude --global
claude --dangerously-skip-permissions << 'EOF'
/gsd:resume-work
/gsd:execute-phase 3
EOF
```

## Summary

- GSD works in Docker and CI via non-interactive install
- Git strategies phase/milestone for team work
- .planning/ in git provides decision history
- Protect sensitive files via deny list
