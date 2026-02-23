---
title: "Обзор курированных навыков"
weight: 5
bookToc: true
---

# Обзор курированных навыков

## Введение

Курированные (curated) навыки — это навыки, проверенные и одобренные командой OpenAI. Они находятся в папке `.curated` репозитория openai/skills и устанавливаются через skill-installer.

## Список курированных навыков

| Навык | Описание |
|-------|----------|
| **figma** | Работа с дизайнами Figma через MCP-сервер |
| **figma-implement-design** | Реализация дизайна из Figma в коде |
| **screenshot** | Создание снимков экрана |
| **gh-fix-ci** | Диагностика и исправление CI в GitHub Actions |
| **gh-address-comments** | Обработка комментариев к PR на GitHub |
| **pdf** | Работа с PDF-документами |
| **doc** | Работа с документами |
| **imagegen** | Генерация изображений |
| **sora** | Генерация видео через Sora |
| **speech** | Синтез речи |
| **transcribe** | Транскрипция аудио |
| **jupyter-notebook** | Работа с Jupyter-ноутбуками |
| **spreadsheet** | Работа с электронными таблицами |
| **playwright** | Автоматизация браузера через Playwright |
| **vercel-deploy** | Деплой на Vercel |
| **netlify-deploy** | Деплой на Netlify |
| **cloudflare-deploy** | Деплой на Cloudflare |
| **render-deploy** | Деплой на Render |
| **linear** | Интеграция с Linear (управление задачами) |
| **sentry** | Интеграция с Sentry (мониторинг ошибок) |
| **notion-meeting-intelligence** | Подготовка заметок для встреч в Notion |
| **notion-knowledge-capture** | Захват знаний в Notion |
| **notion-research-documentation** | Документация исследований в Notion |
| **notion-spec-to-implementation** | Спецификация → реализация через Notion |
| **openai-docs** | Работа с документацией OpenAI |
| **security-best-practices** | Лучшие практики безопасности |
| **security-ownership-map** | Карта владения кодом |
| **security-threat-model** | Моделирование угроз |
| **develop-web-game** | Разработка веб-игр |
| **yeet** | Быстрая публикация кода |

## Как установить курированный навык

```
$skill-installer gh-fix-ci
```

После установки **перезапустите Codex**, чтобы навык стал доступен.

## Как посмотреть список доступных навыков

```
$skill-installer
```

Навыки с пометкой «already installed» уже установлены.

## Итоги

- Курированные навыки проверены OpenAI и готовы к использованию
- Их более 30 — от работы с файлами до деплоя приложений
- Установка — одна команда через skill-installer
- После установки нужен перезапуск Codex
