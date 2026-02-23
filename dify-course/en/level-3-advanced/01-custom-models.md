---
title: "Custom Model Providers"
weight: 1
bookToc: true
---

# Custom Model Providers

## Why Custom Models?

You may want to use models not built into Dify — local models, fine-tuned models, or private endpoints.

## Supported Provider Types

| Type | Examples |
|------|---------|
| **OpenAI-compatible** | vLLM, LocalAI, Together AI |
| **Ollama** | Local models via Ollama |
| **Xinference** | Distributed inference |
| **Custom** | Any API following OpenAI format |

## Adding an OpenAI-Compatible Provider

1. **Settings → Model Providers → OpenAI-API-compatible**
2. Fill in:
   - **Model name**: e.g., `my-llama3`
   - **API URL**: e.g., `http://localhost:8000/v1`
   - **API Key**: if required
3. **Save** and test with a simple prompt

## Using Ollama

```bash
# Install Ollama
curl -fsSL https://ollama.ai/install.sh | sh

# Pull a model
ollama pull llama3

# It runs on localhost:11434
```

In Dify:
1. Add Ollama as a provider
2. URL: `http://host.docker.internal:11434` (if Dify is in Docker)
3. Select models from the list

## Fine-tuned Models

If you've fine-tuned a model (e.g., on OpenAI or Hugging Face):
1. Deploy it with an OpenAI-compatible API
2. Add it as a custom provider in Dify
3. Use it in any app just like a built-in model

## Model Load Balancing

Dify supports adding multiple credentials for the same model. Requests are distributed across them, which helps with rate limits.

1. **Settings → Model Providers → your provider**
2. Add multiple API keys
3. Dify rotates between them automatically

## Next Step

Let's build advanced workflows with complex logic!
