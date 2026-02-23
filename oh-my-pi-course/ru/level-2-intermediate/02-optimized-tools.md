---
title: "Оптимизированные инструменты"
level: 2
lesson: 2
lang: ru
tags: [инструменты, python, lsp, commit, browser]
---

# Оптимизированные инструменты

## Введение

OMP включает набор мощных встроенных инструментов, выходящих далеко за рамки базовых.

## Commit Tool

AI-генерация коммитов с анализом изменений:

```bash
omp commit              # Интерактивный режим
omp commit --push       # Коммит + push
omp commit --dry-run    # Предпросмотр
```

Возможности:
- Разделение несвязанных изменений на атомарные коммиты
- Стейджинг отдельных хунков
- Генерация changelog

## Python Tool

Персистентное IPython-ядро:

```bash
omp setup python  # Установить зависимости
```

Хелперы: `lines()`, `insert_at()`, `delete_lines()`, поиск, shell-команды.

## LSP-интеграция

- Форматирование при записи (rustfmt, prettier, gofmt и т.д.)
- Диагностика после каждого изменения
- 40+ языков из коробки
- Hover-документация, поиск символов

## Browser Tool

Headless-браузер с 14 stealth-скриптами:

- Навигация, клики, скриншоты
- Accessibility-снимки
- Reader mode для извлечения контента

## Task Tool (Субагенты)

6 встроенных агентов для параллельной работы:

- `explore` — исследование кодовой базы
- `plan` — планирование
- `reviewer` — код-ревью
- `task` / `quick_task` — выполнение задач
- `designer` — дизайн

## Web Search & Fetch

Множество провайдеров: Exa, Jina, Perplexity, Anthropic, Gemini и другие.

## Полный список инструментов

`ask`, `bash`, `python`, `calc`, `ssh`, `edit`, `find`, `grep`, `lsp`, `notebook`, `read`, `browser`, `task`, `todo_write`, `fetch`, `web_search`, `write`

## Итоги

OMP предоставляет богатый набор инструментов для любых задач — от коммитов до браузерной автоматизации.
