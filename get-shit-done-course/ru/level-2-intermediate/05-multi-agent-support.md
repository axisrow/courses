---
title: "Работа с разными агентами"
level: 2
lesson: 5
language: ru
tags: [gsd, claude-code, opencode, gemini]
---

# Работа с разными агентами

## Введение

GSD поддерживает три рантайма: Claude Code, OpenCode и Gemini CLI. Установка и команды одинаковые — различается только среда выполнения.

## Инструкции

### Поддерживаемые рантаймы

| Рантайм | Описание | Установка |
|---------|----------|-----------|
| **Claude Code** | Основной, от Anthropic | `--claude` |
| **OpenCode** | Open source, бесплатные модели | `--opencode` |
| **Gemini CLI** | Google Gemini | `--gemini` |

### Установка для конкретного рантайма

```bash
# Только Claude Code
npx get-shit-done-cc --claude --global

# Только OpenCode
npx get-shit-done-cc --opencode --global

# Только Gemini
npx get-shit-done-cc --gemini --global

# Все три
npx get-shit-done-cc --all --global
```

### Расположение файлов

| Рантайм | Глобальный путь |
|---------|-----------------|
| Claude Code | `~/.claude/` |
| OpenCode | `~/.config/opencode/` |
| Gemini | `~/.gemini/` |

### Различия в работе

Основная логика GSD одинакова для всех рантаймов. Различия:
- **Модели** — каждый рантайм использует свои модели
- **Команды** — синтаксис slash-команд может отличаться
- **Подагенты** — реализация параллелизма зависит от рантайма

## Примеры

```bash
# Установить для всех рантаймов
npx get-shit-done-cc --all --global

# Проверить в Claude Code
claude
/gsd:help

# Проверить в OpenCode
opencode
/gsd:help
```

## Итоги

- GSD работает в Claude Code, OpenCode и Gemini CLI
- Одна команда установки с флагами рантайма
- Логика и команды одинаковые
- Можно установить для всех рантаймов сразу
