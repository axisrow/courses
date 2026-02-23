---
title: "Building Custom MCP Servers"
weight: 11
bookToc: true
---

# Building Custom MCP Servers

## Why Build Your Own?

Sentient ships with 20+ integrations, but you may need to connect a service that isn't supported yet — your company's internal API, a niche SaaS tool, or a smart home system.

## MCP Server Structure

Every MCP server in `src/server/mcp_hub/` follows the same pattern:

```
my_service/
├── main.py      # Tool definitions and handlers
├── auth.py      # Authentication logic (OAuth, API keys)
├── utils.py     # Helper functions
├── prompts.py   # System prompts for the AI to understand the tools
└── test_client.py  # Tests
```

## Step-by-Step: Creating a New MCP Server

### 1. Create the folder

```bash
mkdir src/server/mcp_hub/my_service
```

### 2. Define tools in `main.py`

Tools are Python functions that the AI can call. Each tool has:
- A **name** and **description** (so the AI knows when to use it).
- **Parameters** (what input it needs).
- A **handler** (the function that does the work).

```python
async def get_items(query: str) -> dict:
    """Search for items in My Service."""
    response = await client.get(f"/api/items?q={query}")
    return response.json()
```

### 3. Handle authentication in `auth.py`

If your service uses OAuth, follow the pattern from `gmail/auth.py`. For simple API keys, store them in `.env` and read them with `python-dotenv`.

### 4. Write prompts in `prompts.py`

This file contains instructions that tell the AI *when* and *how* to use your tools. Be specific:

```python
SYSTEM_PROMPT = """
Use the my_service tools when the user asks about inventory,
product availability, or order status.
"""
```

### 5. Register the MCP server

Add your new server to the orchestrator configuration so Sentient knows it exists.

### 6. Test

Use `test_client.py` to verify your tools work before connecting them to the AI.

## Best Practices

- Keep tools focused — one tool per action.
- Return structured data (JSON) so the AI can reason about it.
- Handle errors gracefully and return informative messages.
- Write clear prompts — the AI relies on your descriptions.

## Summary

Building a custom MCP server takes about an hour once you understand the pattern. It's the most powerful way to extend Sentient to fit your unique needs.
