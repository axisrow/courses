---
title: "Best Practices"
weight: 5
bookToc: true
---

# Best Practices

## Introduction

Recommendations from Anthropic and the community for creating effective skills.

## Description Quality

```yaml
# ❌ Bad
description: Helps write stuff

# ✅ Good
description: >
  Creates structured technical documentation including API references
  and deployment guides. Use when user needs to write technical docs.
```

## Instructions

- Structure as numbered steps
- Include input → output examples
- Set clear constraints

## Five Rules

1. **One task** — a skill does one thing well
2. **Specific instructions** — no ambiguity
3. **Examples** — show expected output
4. **Testing** — verify with varied inputs
5. **Iteration** — improve based on results

## Folder Structure

```
my-skill/
├── SKILL.md
├── scripts/
├── examples/
├── reference/
└── LICENSE.txt
```

## Summary

- Good description = correct activation
- Structured instructions with examples are key
- One skill = one task
- Test and improve iteratively
