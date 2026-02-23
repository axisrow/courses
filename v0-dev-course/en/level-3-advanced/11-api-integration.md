---
title: "Integrating APIs"
weight: 11
bookToc: true
---

# Integrating APIs

## What is an API?

An API (Application Programming Interface) is a way for your app to talk to other services. For example, fetching weather data, processing payments, or sending emails.

Think of an API like a waiter in a restaurant — you tell the waiter what you want (request), and they bring it from the kitchen (response).

## APIs in v0

v0 can automatically integrate with popular tools and APIs:

- **No account setup needed** for many integrations
- The AI understands common API patterns
- You can describe what data you need in plain language

## How to Add an API Integration

Simply describe it in your prompt:

- "Create a weather widget that shows the current weather for New York"
- "Build a contact form that sends emails via Resend"
- "Make a page that displays the latest news from an RSS feed"

v0 will generate the code with the necessary API calls.

## Popular Integrations

| Service | What It Does |
|---------|-------------|
| Stripe | Payment processing |
| Resend | Email sending |
| OpenAI | AI text generation |
| Supabase | Database and authentication |
| Cloudinary | Image management |

## API Keys

Some APIs require a key (like a password):

1. Sign up for the API service
2. Get your API key from their dashboard
3. Add it to your project's environment variables in Vercel
4. Never put API keys directly in your code

## Summary

APIs let your app connect to external services. v0 makes integration easy — just describe what you need. Next: working with databases.
