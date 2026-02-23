---
title: "AI-модели и LiteLLM"
weight: 8
bookToc: true
---

# AI-модели и LiteLLM

## Выбор «мозга»

Sentient не привязывает вас к одному провайдеру. Благодаря **LiteLLM** вы можете использовать практически любую языковую модель:

- **OpenAI** — GPT-4o, GPT-4, GPT-3.5
- **Google** — Gemini Pro, Gemini Flash
- **Anthropic** — Claude 3.5 Sonnet, Claude 3 Opus
- **Локальные модели** — Llama, Mistral, Qwen через **Ollama**

## Что такое LiteLLM?

LiteLLM — лёгкий прокси между Sentient и AI-провайдером. Он переводит запросы в нужный формат для выбранной модели. Можно переключаться между моделями без изменения кода.

## Настройка

Конфигурация находится в `src/server/litellm-config.yaml`:

```yaml
model_list:
  - model_name: gpt-4o
    litellm_params:
      model: openai/gpt-4o
      api_key: sk-...
```

## Локальные модели через Ollama

Для максимальной конфиденциальности:
1. Установите [Ollama](https://ollama.com).
2. Скачайте модель: `ollama pull qwen2.5`
3. Укажите LiteLLM на локальный Ollama.

Теперь ваши разговоры не покидают компьютер.

## Какую модель выбрать?

| Потребность | Рекомендация |
|---|---|
| Лучшее качество | GPT-4o или Claude 3.5 Sonnet |
| Быстро и дёшево | Gemini Flash или GPT-3.5 |
| Полная конфиденциальность | Qwen 2.5 или Llama 3 через Ollama |
| Баланс | Gemini Pro |

## Итог

LiteLLM даёт Sentient гибкость в выборе моделей — облачных или локальных, быстрых или мощных.
