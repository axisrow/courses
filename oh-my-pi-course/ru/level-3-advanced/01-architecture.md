---
title: "Архитектура (TypeScript + Rust + Bun)"
level: 3
lesson: 1
lang: ru
tags: [архитектура, typescript, rust, bun, монорепо]
---

# Архитектура Oh My Pi

## Введение

OMP — монорепозиторий, сочетающий TypeScript, Rust и Bun для максимальной производительности.

## Стек технологий

- **TypeScript** — основная логика, TUI, агент, SDK
- **Rust** — нативные модули через N-API (~7500 строк)
- **Bun** — рантайм вместо Node.js (быстрее, нативный TypeScript)

## Пакеты монорепо

| Пакет | Описание |
|-------|----------|
| `@oh-my-pi/pi-ai` | Мульти-провайдерный LLM-клиент |
| `@oh-my-pi/pi-agent-core` | Рантайм агента с вызовом инструментов |
| `@oh-my-pi/pi-coding-agent` | CLI и SDK кодинг-агента |
| `@oh-my-pi/pi-tui` | Терминальная UI-библиотека |
| `@oh-my-pi/pi-natives` | N-API биндинги (Rust) |
| `@oh-my-pi/omp-stats` | Дашборд статистики |
| `@oh-my-pi/pi-utils` | Утилиты |

## Нативный движок (Rust)

| Модуль | Строк | Что делает | Библиотека |
|--------|-------|-----------|------------|
| grep | ~1300 | Regex-поиск по файлам | ripgrep internals |
| shell | ~1025 | Встроенный bash | brush-shell |
| text | ~1280 | ANSI-aware обработка текста | unicode-width |
| keys | ~1300 | Kitty keyboard парсер | phf |
| highlight | ~475 | Подсветка синтаксиса | syntect |
| glob | ~340 | Файловый поиск | ignore, globset |
| task | ~350 | Планировщик задач | tokio, napi |
| ps | ~290 | Управление процессами | libc |
| prof | ~250 | Профайлер | inferno |
| image | ~150 | Обработка изображений | image |
| clipboard | ~95 | Буфер обмена | arboard |
| html | ~50 | HTML → Markdown | html-to-markdown-rs |

Платформы: linux-x64, linux-arm64, darwin-x64, darwin-arm64, win32-x64.

## Rust Crates

- `pi-natives` — основной нативный аддон
- `brush-core-vendored` — вендоренный bash-шелл
- `brush-builtins-vendored` — встроенные bash-команды

## Итоги

Архитектура OMP сочетает удобство TypeScript с производительностью Rust, используя Bun как быстрый рантайм.
