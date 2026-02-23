---
title: "API Integration"
weight: 9
bookToc: true
---

# API Integration

Connect your app to external services and APIs.

## What Are APIs?

APIs let your app talk to other services — weather data, payment processors, AI models, and more.

## Fetching External Data

> Fetch the latest news from a public news API and display them as cards.

Lovable generates the fetch logic, loading states, and error handling.

## Supabase Edge Functions

For server-side logic, use Supabase Edge Functions:

> Create an edge function that calls the OpenAI API and returns a summary of the given text.

Edge Functions run on the server, keeping your API keys safe.

## Environment Variables

Store API keys securely:

> Store the API key in an environment variable. Don't hardcode it.

Lovable uses Supabase secrets for server-side keys.

## Common Integrations

| Service | Use Case |
|---------|----------|
| Stripe | Payments and subscriptions |
| OpenAI | AI-powered features |
| SendGrid | Email notifications |
| Cloudinary | Image upload and processing |
| Google Maps | Location and maps |

## Webhooks

> When a new order is created, send a webhook to our Slack channel.

## Error Handling

> Show a friendly error message if the API call fails. Add a retry button.

## Summary

APIs expand what your app can do. Use Supabase Edge Functions for secure server-side calls. Lovable handles the integration code for you.
