---
title: "Model Configuration"
weight: 10
bookToc: true
---

# Model Configuration

## Why Model Configuration Matters

Nexent is model-agnostic — it works with many different AI model providers. Choosing the right model affects response quality, speed, and cost.

## Supported Providers

Nexent supports several model providers:

- **OpenAI** (GPT-4, GPT-3.5, etc.)
- **SiliconFlow**
- **ModelEngine**
- **Other OpenAI-compatible APIs**

## Adding a Model Provider

1. Go to **Settings → Model Providers**.
2. Click **Add Provider**.
3. Select the provider type.
4. Enter your API key and endpoint URL.
5. Test the connection.
6. Save.

## Choosing Models for Different Tasks

Nexent uses models for several purposes:

| Task | Recommended Model |
|------|------------------|
| Chat / Conversation | GPT-4 or equivalent (best quality) |
| Document summarization | GPT-3.5 or equivalent (good balance of speed and quality) |
| Embeddings | Text-embedding model (for knowledge base search) |
| Image understanding | Vision-capable model (GPT-4V or equivalent) |

## Model Health Monitoring

Nexent includes a model health checker that monitors:

- Response times.
- Error rates.
- Availability.

If a model becomes unavailable, Nexent can alert you so you can switch to a backup.

## Cost Management Tips

- Use smaller, cheaper models for simple tasks (summarization, classification).
- Reserve powerful models for complex reasoning and multi-step tasks.
- Monitor your API usage in the provider's dashboard.

## Practice Exercise

1. Check which model providers are configured in your Nexent installation.
2. Add a new provider (or a second model from the same provider).
3. Assign different models to different tasks.
4. Compare response quality between models.

Congratulations on completing Level 2! 🎉
