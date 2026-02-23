---
title: "Интеграция с разными IDE"
level: 2
lesson: 5
lang: ru
---

# Интеграция с разными IDE

## Введение

Особенности работы с Claude Code, Cursor, Codex и OpenCode.

## Claude Code

Основная платформа с лучшей поддержкой:

- Маркетплейс плагинов
- Нативная поддержка субагентов
- Автообновление навыков

```bash
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace
/plugin update superpowers
```

## Cursor

Интеграция через Agent chat:

```
/plugin-add superpowers
```

Особенности:
- Работает в режиме Agent (не Ask)
- Субагенты через встроенный механизм Cursor

## Codex

Ручная установка через fetch инструкций:

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

Особенности:
- Требует ручной настройки
- Меньше автоматизации

## OpenCode

Аналогично Codex:

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md
```

## Сравнение платформ

| Возможность | Claude Code | Cursor | Codex | OpenCode |
|------------|-------------|--------|-------|----------|
| Маркетплейс | ✓ | ✓ | ✗ | ✗ |
| Автообновление | ✓ | ✓ | ✗ | ✗ |
| Субагенты | ✓ | ✓ | Частично | Частично |
| Простота | ★★★ | ★★★ | ★★ | ★★ |

## Итоги

- Claude Code — лучшая интеграция
- Cursor — хороший вариант с GUI
- Codex и OpenCode — требуют ручной настройки
- Все платформы поддерживают основной workflow
