---
title: "Установка GSD"
level: 1
lesson: 2
language: ru
tags: [gsd, установка, npx]
---

# Установка GSD

## Введение

GSD устанавливается одной командой через npx. Не нужно клонировать репозиторий или настраивать зависимости.

## Инструкции

### Быстрая установка

```bash
npx get-shit-done-cc@latest
```

Установщик спросит:
1. **Runtime** — Claude Code, OpenCode, Gemini или все сразу
2. **Расположение** — Глобально (все проекты) или локально (текущий проект)

### Неинтерактивная установка

```bash
# Claude Code глобально
npx get-shit-done-cc --claude --global

# OpenCode глобально
npx get-shit-done-cc --opencode --global

# Gemini CLI глобально
npx get-shit-done-cc --gemini --global

# Все рантаймы
npx get-shit-done-cc --all --global
```

### Проверка установки

Откройте Claude Code и введите:

```
/gsd:help
```

Если видите список команд — всё работает.

## Примеры

```bash
# Установка для Claude Code в текущий проект
npx get-shit-done-cc --claude --local

# Обновление до последней версии
npx get-shit-done-cc@latest
```

## Итоги

- Установка через `npx get-shit-done-cc@latest`
- Выбираете runtime и расположение (глобально/локально)
- Проверяете через `/gsd:help`
- Обновляете той же командой с `@latest`
