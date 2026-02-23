---
title: "Using Skills in Claude Code, Claude.ai, and API"
weight: 2
bookToc: true
---

# Using Skills

## Introduction

Skills can be used three ways: in Claude Code (CLI), in the Claude.ai web interface, and via the API.

## Claude Code

### Adding the marketplace

```bash
/plugin marketplace add anthropics/skills
```

### Installing a skill

```bash
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

### Usage

After installation, just mention the task:

> "Use the PDF skill to extract form fields from report.pdf"

## Claude.ai

Skills are already available for paid plans in Claude.ai. To upload custom skills, go to project settings and upload your skill folder.

## Claude API

Skills are available via the API. See the [Skills API Quickstart](https://docs.claude.com/en/api/skills-guide) for details.

## Summary

- Claude Code: install via `/plugin` commands
- Claude.ai: built-in for paid plans
- API: connect through request parameters
- Skills activate automatically when a relevant task is mentioned
