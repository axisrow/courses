---
title: "MCP HTTP Server"
weight: 13
bookToc: true
---

# MCP HTTP Server

## Stdio vs HTTP

By default, QMD's MCP server runs as a subprocess (stdio mode). Each client launches its own copy, loading AI models each time. For a shared, always-on server, use HTTP transport.

## Starting the HTTP Server

```sh
# Foreground (Ctrl-C to stop)
qmd mcp --http                    # listens on localhost:8181
qmd mcp --http --port 8080        # custom port

# Background daemon
qmd mcp --http --daemon           # starts in background
```

## Stopping the Server

```sh
qmd mcp stop                      # stops the daemon
```

## Checking Status

```sh
qmd status
# Shows "MCP: running (PID ...)" when active
```

## HTTP Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/mcp` | POST | MCP Streamable HTTP (JSON, stateless) |
| `/health` | GET | Liveness check with uptime |

## Connecting Clients

Point any MCP-compatible client to:

```
http://localhost:8181/mcp
```

## Performance Benefits

The HTTP server keeps AI models loaded in GPU memory across requests. This means:

- **First request**: ~1 second (model context creation)
- **Subsequent requests**: near-instant
- **Idle timeout**: embedding/reranking contexts are released after 5 minutes of inactivity, then recreated transparently on next use

## When to Use HTTP Mode

Use HTTP mode when:
- Multiple AI agents need to access QMD simultaneously
- You want models to stay loaded for faster responses
- You're building a service that queries QMD regularly

Use stdio mode when:
- You have a single AI client (like Claude Desktop)
- You don't want a long-running process
- Simplicity is more important than speed

## Security Note

The HTTP server listens on `localhost` only. It's not exposed to the network by default. If you need remote access, use a reverse proxy with authentication.

## Next Steps

Let's learn about the smart chunking algorithm and how to tune it for your content.
