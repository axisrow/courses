---
title: "Skills & Tools"
weight: 2
bookToc: true
---

# Skills & Tools

## Introduction

**Skills** and **Tools** are what make DeerFlow truly versatile. Skills define *what* the agent can do, while tools define *how* it does it.

## Skills

### What is a Skill?

A **skill** is a Markdown file with instructions that describes a step-by-step process for a specific type of task. Think of it as a detailed job description for the AI agent.

### Built-in Skills

| Skill | Description |
|-------|-------------|
| `research` | Deep topic research with source citations |
| `report-generation` | Creating structured reports |
| `slide-creation` | Generating presentations |
| `web-page` | Creating HTML/CSS web pages |
| `image-generation` | Generating images |

### Where Skills Are Stored

```
deer-flow/skills/
├── public/                    ← built-in skills
│   ├── research/SKILL.md
│   ├── report-generation/SKILL.md
│   └── ...
└── custom/                    ← your skills (add here)
    └── your-skill/SKILL.md
```

### SKILL.md Structure

```markdown
---
name: my-skill
description: "Skill description"
license: MIT
allowed-tools:
  - web_search
  - write_file
---

# Instructions for the agent

Step-by-step process...
```

### Progressive Loading

Skills are loaded **only when needed**. This keeps the context window lean and works well with token-sensitive models.

## Tools

### Types of Tools

1. **Built-in** — shipped with DeerFlow (bash, ls, read_file, write_file, etc.)
2. **Community** — from the community (tavily, jina_ai, firecrawl, image_search)
3. **MCP** — connected via the MCP standard
4. **Custom** — your own Python functions

### Configuring Tools in config.yaml

```yaml
tools:
  - name: web_search
    group: web
    use: src.community.tavily.tools:web_search_tool

tool_groups:
  - name: web
  - name: file:read
  - name: file:write
  - name: bash
```

## MCP Servers

**MCP** (Model Context Protocol) is a standard protocol for connecting external tools:

```json
{
  "mcpServers": {
    "github": {
      "enabled": true,
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_TOKEN": "your-token" }
    }
  }
}
```

Connection types: `stdio` (runs a program), `sse` (URL via SSE), `http` (URL via HTTP).

## Managing Skills via API

- `GET /api/skills` — list all skills
- `PUT /api/skills/{name}` — enable/disable
- `POST /api/skills/install` — install from .skill archive

## Summary

- Skills are Markdown instructions that extend the agent's capabilities
- Tools are functions the agent calls to perform actions
- Skills load progressively to save context
- MCP allows connecting external tools
- You can create your own skills and tools
