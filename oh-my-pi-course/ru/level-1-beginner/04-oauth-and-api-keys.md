---
title: "OAuth и API-ключи"
level: 1
lesson: 4
lang: ru
tags: [api, oauth, провайдеры, аутентификация]
---

# OAuth и API-ключи

## Введение

Для работы OMP нужен доступ к AI-провайдеру. Есть два способа: переменные окружения и интерактивный `/login`.

## Способ 1: Переменные окружения

Экспортируйте ключ нужного провайдера:

```bash
# Anthropic (Claude)
export ANTHROPIC_API_KEY="sk-ant-..."

# OpenAI
export OPENAI_API_KEY="sk-..."

# Google Gemini
export GEMINI_API_KEY="..."

# xAI (Grok)
export XAI_API_KEY="..."

# OpenRouter (доступ к множеству моделей)
export OPENROUTER_API_KEY="..."
```

Добавьте строку в `~/.bashrc` или `~/.zshrc` для постоянного хранения.

## Способ 2: Интерактивный /login

```bash
omp
/login
```

Поддерживаемые провайдеры для OAuth:

- Anthropic (Claude Pro/Max)
- ChatGPT Plus/Pro (Codex)
- GitHub Copilot
- Google Cloud Code Assist
- Cursor
- Perplexity
- Ollama (локальный)
- и многие другие

## Поведение учётных данных

- `/login` **добавляет** учётные данные (не удаляет существующие)
- `/logout` очищает данные для выбранного провайдера
- Данные хранятся в `~/.omp/agent/agent.db`
- API-ключи имеют приоритет над OAuth

## Локальные модели (Ollama)

```bash
# Установить Ollama
curl -fsSL https://ollama.com/install.sh | sh

# Скачать модель
ollama pull llama3.1

# В OMP
omp
/login
# Выбрать ollama
```

API-ключ для Ollama необязателен.

## Итоги

Настройте API-ключ через переменную окружения или `/login`. Можно использовать несколько провайдеров одновременно.
