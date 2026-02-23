---
title: "API Integration"
weight: 2
bookToc: true
---

# API Integration

## Using the Dify API

Every published app exposes a REST API. This lets you integrate AI into your own products.

## Authentication

All requests need an API key in the header:

```
Authorization: Bearer app-xxxxxxxxxxxx
```

Find your key in **Studio → your app → API Access**.

## Chat API

### Send a Message

```bash
curl -X POST 'https://api.dify.ai/v1/chat-messages' \
  -H 'Authorization: Bearer app-xxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "inputs": {},
    "query": "What is Dify?",
    "user": "user-123",
    "conversation_id": ""
  }'
```

### Streaming Response

Add `"response_mode": "streaming"` to get Server-Sent Events (SSE):

```json
{
  "query": "Tell me about Dify",
  "response_mode": "streaming",
  "user": "user-123"
}
```

## Completion API (Text Generator)

```bash
curl -X POST 'https://api.dify.ai/v1/completion-messages' \
  -H 'Authorization: Bearer app-xxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "inputs": {"topic": "AI trends"},
    "user": "user-123"
  }'
```

## Key Endpoints

| Endpoint | Purpose |
|----------|---------|
| `POST /chat-messages` | Send chat message |
| `GET /conversations` | List conversations |
| `GET /messages` | Get message history |
| `POST /completion-messages` | Text generation |
| `POST /files/upload` | Upload files |

## Rate Limits

The cloud version has rate limits per plan. Self-hosted has no limits by default, but you should add your own.

## Next Step

Let's build complex logic with workflows!
