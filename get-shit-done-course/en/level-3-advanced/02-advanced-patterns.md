---
title: "Advanced Patterns"
level: 3
lesson: 2
language: en
tags: [gsd, patterns, advanced]
---

# Advanced Patterns

## Introduction

Once you've mastered the basics, you can use advanced GSD patterns for complex projects.

## Instructions

### Brownfield Projects

For existing codebases:

```
/gsd:map-codebase
```

This spawns parallel agents that analyze your tech stack, architecture, code conventions, and potential issues. After mapping, `/gsd:new-project` accounts for existing code.

### Inserting Urgent Phases

```
/gsd:insert-phase 3
```

Inserts a phase between existing ones, renumbering the rest. Useful for hotfixes.

### Milestone Management

```
/gsd:complete-milestone   # Finish, archive, tag
/gsd:new-milestone        # Start new cycle
/gsd:audit-milestone      # Verify goals achieved
```

### Debug Mode

```
/gsd:debug "Auth breaks on repeated login"
```

Systematic debugging with persistent state.

### Quick Mode with Full Verification

```
/gsd:quick --full
```

Quick tasks with plan checking and verification.

### Skipping Steps

```
/gsd:plan-phase 1 --skip-research
/gsd:plan-phase 1 --skip-verify
```

## Examples

Typical workflow for a mature project:
```
/gsd:map-codebase
/gsd:new-milestone "v2.0"
/gsd:discuss-phase 1
/gsd:plan-phase 1
/gsd:execute-phase 1
/gsd:verify-work 1
/gsd:insert-phase 2          # Urgent fix
/gsd:plan-phase 2
```

## Summary

- `/gsd:map-codebase` for existing projects
- Insert urgent phases with `insert-phase`
- Milestones for versioning
- Debug mode for systematic debugging
- Quick --full for fast tasks with verification
