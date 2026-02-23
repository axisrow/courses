---
title: "Publishing Your App"
weight: 5
bookToc: true
---

# Publishing Your App

## Overview

Once your app works well in preview, it's time to share it with users.

## Publishing Options

### 1. Web App (Built-in)

Click **Publish** in the top-right corner. Dify generates a shareable URL.

- Anyone with the link can use your app
- No coding required
- Looks professional out of the box

### 2. Embed in Website

Click **Embed** to get code snippets:

```html
<iframe
  src="https://your-dify-instance.com/chatbot/abc123"
  width="400"
  height="600"
  frameborder="0">
</iframe>
```

### 3. API Access

Every app gets an API endpoint. Go to **API Access** to find:

- Your API key
- Endpoint URL
- Example requests

```bash
curl -X POST 'https://api.dify.ai/v1/chat-messages' \
  -H 'Authorization: Bearer YOUR_API_KEY' \
  -H 'Content-Type: application/json' \
  -d '{"query": "Hello!", "user": "user-1"}'
```

## App Settings

Before publishing, review:

- **Name & Description** — clear for end users
- **Icon** — choose or upload one
- **Rate Limits** — prevent abuse
- **Copyright** — add your info

## Monitoring Usage

After publishing, check the **Logs** section to see:

- User messages and AI responses
- Token usage and costs
- Errors or issues

## Congratulations! 🎉

You've completed Level 1. You can now:
- ✅ Install and set up Dify
- ✅ Build AI apps
- ✅ Write effective prompts
- ✅ Publish and share your apps

**Next: Level 2** — Knowledge bases, APIs, workflows, and more.
