---
title: "Frontmatter and Metadata"
weight: 2
bookToc: true
---

# Frontmatter and Metadata

## Introduction

Frontmatter is the YAML block at the top of `SKILL.md` that defines skill metadata. Its quality determines when and how Claude activates the skill.

## Required Fields

### name

```yaml
name: my-skill-name
```

Rules: lowercase letters, hyphens only, unique.

### description

The most important field:

```yaml
description: >
  Guide for creating MCP servers that enable LLMs to interact 
  with external services. Use when building MCP servers.
```

A good description includes: what it does, when to use it, keywords for activation.

## Examples

❌ Bad: `description: Helps with code`

✅ Good: `description: Reviews Python code for security vulnerabilities and PEP 8 compliance. Use when user asks to review or audit Python code.`

## Summary

- Frontmatter determines when Claude activates a skill
- `name` — unique skill ID
- `description` — the key field for correct activation
- Include triggers and keywords in the description
