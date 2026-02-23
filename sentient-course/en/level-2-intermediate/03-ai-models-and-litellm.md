---
title: "AI Models and LiteLLM"
weight: 8
bookToc: true
---

# AI Models and LiteLLM

## Choosing Your Brain

Sentient doesn't lock you into one AI provider. Thanks to **LiteLLM**, a lightweight proxy, you can use almost any language model:

- **OpenAI** — GPT-4o, GPT-4, GPT-3.5
- **Google** — Gemini Pro, Gemini Flash
- **Anthropic** — Claude 3.5 Sonnet, Claude 3 Opus
- **Local models** — Llama, Mistral, Qwen via **Ollama**

## What Is LiteLLM?

LiteLLM sits between Sentient and the AI provider. It translates Sentient's requests into the correct format for whichever model you've chosen. This means you can switch models without changing any code.

## Configuring Models

The LiteLLM configuration lives in `src/server/litellm-config.yaml`. Here you define:

```yaml
model_list:
  - model_name: gpt-4o
    litellm_params:
      model: openai/gpt-4o
      api_key: sk-...
  - model_name: gemini-pro
    litellm_params:
      model: google/gemini-pro
      api_key: ...
```

## Running Models Locally with Ollama

For maximum privacy, you can run models on your own hardware:

1. Install [Ollama](https://ollama.com).
2. Pull a model: `ollama pull qwen2.5`
3. Sentient includes a `Modelfile` in the repo root for custom model configurations.
4. Point LiteLLM to your local Ollama endpoint.

Now your conversations never leave your machine.

## Which Model Should I Choose?

| Need | Recommended |
|---|---|
| Best quality, cost doesn't matter | GPT-4o or Claude 3.5 Sonnet |
| Fast and cheap | Gemini Flash or GPT-3.5 |
| Full privacy (local) | Qwen 2.5 or Llama 3 via Ollama |
| Balanced | Gemini Pro |

## Summary

LiteLLM gives Sentient model flexibility. You pick the AI brain that fits your needs — cloud or local, fast or powerful.
