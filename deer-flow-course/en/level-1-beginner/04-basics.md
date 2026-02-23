---
title: "Working Basics"
weight: 4
bookToc: true
---

# Working Basics

## Introduction

Now that you've tried DeerFlow in action, let's understand the core concepts and learn to use the system effectively.

## File System Structure

DeerFlow works with a virtual file system. Each session (conversation) gets its own set of folders:

```
/mnt/user-data/
├── uploads/      ← your uploaded files go here
├── workspace/    ← agent's working directory
└── outputs/      ← final deliverables for you
```

> A **virtual file system** is a set of folders that exists inside the container (sandbox). It's isolated from files on your computer.

## Agent Tools

| Tool | Description |
|------|-------------|
| `web_search` | Internet search |
| `web_fetch` | Load web page content |
| `bash` | Run terminal commands |
| `read_file` | Read files |
| `write_file` | Create and write files |
| `str_replace` | Replace text in files |
| `ls` | List folder contents |
| `present_files` | Show output files to user |
| `view_image` | View images |

The agent automatically chooses which tools to use — just describe your task.

## Configuration: config.yaml

The main settings file is `config.yaml` in the project root:

### Models

```yaml
models:
  - name: gpt-4o
    display_name: GPT-4o
    use: langchain_openai:ChatOpenAI
    model: gpt-4o
    api_key: $OPENAI_API_KEY   # $ means the value comes from environment
```

### Sandbox

```yaml
sandbox:
  use: src.sandbox.local:LocalSandboxProvider    # Local
  # or
  use: src.community.aio_sandbox:AioSandboxProvider  # Docker
```

## Skills

**Skills** are specialized instructions that extend the agent's capabilities. Built-in skills include: research, report-generation, slide-creation, web-page, and image-generation.

Skills are loaded **progressively** — only when needed for the current task.

## Extensions: extensions_config.json

This file manages additional tools via **MCP** (Model Context Protocol) — a standard for connecting external tools to AI agents.

```json
{
  "mcpServers": {
    "my-tool": {
      "enabled": true,
      "type": "stdio",
      "command": "npx",
      "args": ["my-mcp-server"]
    }
  }
}
```

## Streaming Output

DeerFlow shows results in real time via **SSE** (Server-Sent Events). You'll see which tools are being called, intermediate results, and sub-agent progress.

## Summary

- DeerFlow uses a virtual file system for each session
- The agent automatically selects needed tools
- Settings are stored in `config.yaml` and `extensions_config.json`
- Skills extend the agent's capabilities
- Results are displayed in real time
