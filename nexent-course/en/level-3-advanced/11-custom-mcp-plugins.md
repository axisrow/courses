---
title: "Building Custom MCP Plugins"
weight: 11
bookToc: true
---

# Building Custom MCP Plugins

## Why Build Custom Plugins?

While Nexent comes with many built-in tools, you may need to connect your agent to a proprietary system — your CRM, internal database, or a custom API. MCP plugins let you extend Nexent with any capability you can imagine.

## What Is an MCP Plugin?

An MCP plugin is a Python service that follows the Model Context Protocol specification. It exposes one or more **tools** that agents can call during conversations.

## Plugin Structure

A typical MCP plugin has:

```
my-plugin/
├── server.py       # The main service file
├── requirements.txt
└── README.md
```

The `server.py` file defines the tools your plugin provides.

## Creating a Simple Plugin

Here's a simplified example — a tool that returns the current date:

```python
from datetime import date

def get_today():
    """Return today's date in YYYY-MM-DD format."""
    return {"date": str(date.today())}
```

In practice, you wrap this in an MCP-compatible server that Nexent can communicate with.

## Registering Your Plugin

1. Host your plugin as a service (locally or on a server).
2. In Nexent, go to **Settings → Tools → Add Remote MCP Tool**.
3. Enter the URL where your plugin is running.
4. Nexent discovers the available tools and makes them selectable for agents.

## Best Practices

- **One tool per action.** Keep tools focused and simple.
- **Clear descriptions.** Write good docstrings — the AI reads them to decide when to use the tool.
- **Error handling.** Return helpful error messages so the agent can explain failures.
- **Security.** Never expose sensitive credentials in tool responses.

## Testing Your Plugin

1. Run the plugin locally.
2. Register it in Nexent.
3. Create an agent with access to the new tool.
4. Ask the agent a question that should trigger the tool.
5. Verify the response includes data from your plugin.

## Practice Exercise

Build a simple MCP plugin that returns a random motivational quote. Register it in Nexent and create an agent that shares a daily quote when asked.
