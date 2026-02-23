---
title: "Skill-installer: установщик навыков"
weight: 2
bookToc: true
---

# Skill-installer: установщик навыков

## Введение

Skill-installer — это встроенный системный навык Codex, который управляет установкой других навыков. В этом уроке мы разберём все его возможности.

## Основные команды

### Показать список навыков

```
$skill-installer
```

Результат:
```
Skills from openai/skills:
1. figma
2. screenshot (already installed)
3. gh-fix-ci
...
Which ones would you like installed?
```

### Установить курированный навык по имени

```
$skill-installer gh-address-comments
```

### Установить из другой папки

```
$skill-installer install the create-plan skill from the .experimental folder
```

### Установить из любого GitHub-репозитория

```
$skill-installer install https://github.com/user/repo/tree/main/my-skill
```

## Что происходит при установке

1. Skill-installer скачивает папку навыка с GitHub
2. Копирует её в `~/.codex/skills/имя-навыка/`
3. Если навык уже установлен — установка прерывается
4. После установки нужно перезапустить Codex

## Работа с приватными репозиториями

Если навык находится в приватном репозитории:

1. Skill-installer попробует использовать ваши git-данные
2. Можно задать `GITHUB_TOKEN` или `GH_TOKEN`
3. Сначала пробуется HTTPS, затем SSH

## Технические детали

Под капотом skill-installer использует три Python-скрипта:

- `list-skills.py` — получает список навыков с GitHub API
- `install-skill-from-github.py` — скачивает и устанавливает навык
- `github_utils.py` — вспомогательные функции для работы с GitHub

## Итоги

- Skill-installer — универсальный инструмент для установки навыков
- Работает с курированными, экспериментальными и сторонними навыками
- Поддерживает приватные репозитории
- После установки всегда перезапускайте Codex
