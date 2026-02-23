---
title: "Tools & Plugins"
weight: 4
bookToc: true
---

# Tools & Plugins

## What Are Tools?

Tools let your AI app interact with the outside world — search the web, query databases, call APIs, and more.

## Built-in Tools

Dify includes several tools out of the box:

| Tool | What It Does |
|------|-------------|
| **Web Search** | Search Google/Bing/DuckDuckGo |
| **Wikipedia** | Query Wikipedia articles |
| **Web Scraper** | Extract content from URLs |
| **Calculator** | Perform math calculations |
| **Current Time** | Get the current date/time |

## Enabling Tools

1. Go to **Studio → your app**
2. Switch to **Agent** mode (tools only work with agents)
3. In the **Tools** section, click **Add Tool**
4. Select from the list and configure credentials if needed

## Custom Tools (API-based)

You can add any REST API as a custom tool:

1. Go to **Tools → Custom → Create**
2. Paste an **OpenAPI/Swagger** schema
3. Configure authentication (API key, Bearer token, etc.)
4. Test the tool
5. Save — it's now available in all your apps

### Example: Weather API

```yaml
openapi: 3.0.0
info:
  title: Weather API
paths:
  /weather:
    get:
      summary: Get weather for a city
      parameters:
        - name: city
          in: query
          required: true
          schema:
            type: string
```

## Agent Mode

When you add tools to an agent app, the AI decides when to use them. For example:

- User asks "What's the weather in Tokyo?" → AI calls the weather tool
- User asks "Tell me a joke" → AI responds directly, no tool needed

## Next Step

Let's learn about team collaboration in Dify!
