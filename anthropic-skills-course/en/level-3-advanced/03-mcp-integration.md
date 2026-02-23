---
title: "MCP Integration"
weight: 3
bookToc: true
---

# MCP Integration

## Introduction

MCP (Model Context Protocol) connects LLMs to external services. The `mcp-builder` skill helps create MCP servers.

## Skills + MCP

| Skills | MCP |
|--------|-----|
| Instructions and processes | Service connections |
| Text rules | Programmatic interfaces |
| Static knowledge | Dynamic data |

## The mcp-builder Skill

```
mcp-builder/
├── SKILL.md
└── reference/
    ├── evaluation.md
    ├── python_mcp_server.md
    └── mcp_best_practices.md
```

Creates MCP servers in Python (FastMCP) or TypeScript (MCP SDK).

## Combining Skills and MCP

A skill can instruct Claude to use MCP tools:

```markdown
---
name: database-reporter
description: Creates database reports using MCP database tools
---

# Process
1. Connect using MCP tool `query_db`
2. Execute analysis query
3. Format results as markdown table
```

## Summary

- MCP connects LLMs to external services
- `mcp-builder` helps create MCP servers
- Skills and MCP complement each other
