---
title: "Webhooks and Integrations"
weight: 12
bookToc: true
---

# Webhooks and Integrations

## What Are Webhooks?

Webhooks are "reverse APIs." Instead of you asking for data, the service sends data to you when something happens.

## Setting Up a Webhook in n8n

1. Add a **Webhook** node as the trigger
2. Choose the HTTP method (GET or POST)
3. Copy the **Webhook URL** (two versions: test and production)
4. Use the test URL during development, production URL when active

### Webhook Settings
- **Path** — Custom URL path (e.g., `/form-submit`)
- **Method** — GET, POST, PUT, DELETE
- **Authentication** — None, Basic Auth, Header Auth
- **Response Mode** — Respond immediately or after workflow finishes
- **Response Data** — Custom JSON response to send back

## Receiving Data

When a webhook receives a POST request, the data is available in:
- `{{ $json.body }}` — Request body
- `{{ $json.headers }}` — Request headers
- `{{ $json.query }}` — URL query parameters

## Responding to Webhooks

### Immediate Response
```
Webhook → Respond to Webhook node → Return custom JSON
```

### After Processing
```
Webhook → Process data → Respond to Webhook → Return result
```

The **Respond to Webhook** node lets you send a custom response:
```json
{
  "status": "success",
  "message": "Data received",
  "id": "{{ $json.id }}"
}
```

## Real-World Integrations

### GitHub → Slack Notifications
```
Webhook (receives GitHub events)
  → IF (event type = "push")
  → Set (format message)
  → Slack (send to #dev channel)
```

### Stripe → Database
```
Webhook (receives Stripe payment events)
  → IF (event = "payment_intent.succeeded")
  → Set (extract amount, customer)
  → Postgres (insert payment record)
```

### Form → Email + Sheet
```
Webhook (receives form data)
  → Google Sheets (save submission)
  → Gmail (send confirmation email)
```

## Building a Simple API with n8n

You can use n8n as a lightweight API server:

```
GET /api/users    → Webhook → Postgres (SELECT) → Respond to Webhook
POST /api/users   → Webhook → Postgres (INSERT) → Respond to Webhook
```

## Security

- **Use authentication** on webhooks (Basic Auth or Header Auth)
- **Validate incoming data** before processing
- **Use HTTPS** in production
- **Check webhook signatures** for services that provide them (like Stripe and GitHub)

## Practice

1. Create a webhook that accepts POST data
2. Validate that `name` and `email` fields exist
3. Save to a Google Sheet (or Set node for testing)
4. Return a success response with an ID

## Summary

You can now build webhook-powered integrations. Next, you will learn about performance and scaling.
