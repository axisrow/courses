---
title: "Using QMD with AI Agents"
weight: 9
bookToc: true
---

# Using QMD with AI Agents

## Why Connect QMD to AI?

AI assistants like Claude are powerful, but they don't know about *your* files. QMD bridges this gap — it lets AI tools search your personal knowledge base.

## Command-Line Integration

The simplest approach: just tell your AI agent to run QMD commands. The `--json` and `--files` flags produce clean output that AI can parse:

```sh
# Structured results for an LLM
qmd search "authentication" --json -n 10

# List all relevant files above a threshold
qmd query "error handling" --all --files --min-score 0.4

# Retrieve full document content
qmd get "docs/api-reference.md" --full
```

## MCP Server

MCP (Model Context Protocol) is a standard way for AI tools to connect to data sources. QMD has a built-in MCP server.

### Available MCP Tools

| Tool | Description |
|------|-------------|
| `qmd_search` | Fast BM25 keyword search |
| `qmd_vector_search` | Semantic vector search |
| `qmd_deep_search` | Deep search with query expansion and reranking |
| `qmd_get` | Retrieve document by path or ID |
| `qmd_multi_get` | Retrieve multiple documents |
| `qmd_status` | Index health and collection info |

### Setting Up with Claude Desktop

Add this to your Claude Desktop configuration file:

```json
{
  "mcpServers": {
    "qmd": {
      "command": "qmd",
      "args": ["mcp"]
    }
  }
}
```

**Config file location**: `~/Library/Application Support/Claude/claude_desktop_config.json`

### Setting Up with Claude Code

```bash
claude marketplace add tobi/qmd
claude plugin add qmd@qmd
```

## How It Works

Once connected, you can ask Claude things like:

- "Search my notes for anything about the Q4 budget"
- "Find all meeting transcripts about the product launch"
- "What did I write about database migrations?"

Claude will use QMD's MCP tools automatically to search your documents and provide answers based on your content.

## Next Steps

Let's learn about index maintenance and keeping your QMD setup healthy.
