---
title: "Конфигурация"
level: 2
lesson: 3
lang: ru
tags: [конфигурация, настройки, config.yml]
---

# Конфигурация

## Введение

OMP настраивается через файлы конфигурации на глобальном и проектном уровне.

## Глобальная конфигурация

Файл: `~/.omp/agent/config.yml`

```yaml
theme:
  dark: titanium
  light: light

modelRoles:
  default: anthropic/claude-sonnet-4-20250514

defaultThinkingLevel: medium

compaction:
  enabled: true
  reserveTokens: 16384
  keepRecentTokens: 20000
  autoContinue: true

skills:
  enabled: true

terminal:
  showImages: true
```

## Управление через CLI

```bash
omp config list           # Все настройки
omp config get theme      # Получить значение
omp config set theme.dark dracula  # Установить
omp config reset theme    # Сбросить
omp config path           # Путь к файлу
```

## Контекстные файлы проекта

OMP загружает контекст из нескольких директорий:

- `.omp/` — основная
- `.claude/`, `.codex/`, `.gemini/` — совместимость с другими инструментами

Файлы `AGENTS.md`, `CLAUDE.md` используются для инструкций проекту.

## Кастомный системный промпт

1. **Проектный:** `.omp/SYSTEM.md`
2. **Глобальный:** `~/.omp/agent/SYSTEM.md`

```bash
omp --system-prompt "Ты эксперт по Python"
omp --append-system-prompt "Всегда пиши тесты"
```

## Кастомные модели

Файл `~/.omp/agent/models.yml`:

```yaml
providers:
  ollama:
    baseUrl: http://localhost:11434/v1
    api: openai-completions
    models:
      - id: llama-3.1-8b
        name: Llama 3.1 8B
        contextWindow: 128000
        maxTokens: 32000
```

## Темы

65+ встроенных тем. Кастомные: `~/.omp/agent/themes/*.json`.

## Итоги

Конфигурация OMP гибкая — от глобальных настроек до проектных контекстов и кастомных моделей.
