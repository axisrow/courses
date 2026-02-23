---
title: "Установка Superpowers"
level: 1
lesson: 2
lang: ru
---

# Установка Superpowers

## Введение

Как установить Superpowers в Claude Code, Cursor, Codex и OpenCode.

## Установка

### Claude Code (рекомендуется)

Claude Code имеет встроенный маркетплейс плагинов.

```bash
# Шаг 1: добавьте маркетплейс
/plugin marketplace add obra/superpowers-marketplace

# Шаг 2: установите плагин
/plugin install superpowers@superpowers-marketplace
```

### Cursor

В чате Cursor Agent:

```
/plugin-add superpowers
```

### Codex

Скажите Codex:

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

### OpenCode

Скажите OpenCode:

```
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md
```

## Проверка установки

Откройте новую сессию и попросите агента что-нибудь спланировать:

```
Помоги мне спланировать новую фичу
```

Если Superpowers работает, агент начнёт задавать уточняющие вопросы вместо того, чтобы сразу писать код.

## Обновление

```bash
/plugin update superpowers
```

## Итоги

- Установка зависит от платформы
- Claude Code и Cursor — через маркетплейс
- Codex и OpenCode — через ручные инструкции
- Проверьте установку, попросив агента спланировать фичу
