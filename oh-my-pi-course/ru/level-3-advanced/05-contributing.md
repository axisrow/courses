---
title: "Контрибьюция"
level: 3
lesson: 5
lang: ru
tags: [контрибьюция, open source, PR, разработка]
---

# Контрибьюция в Oh My Pi

## Введение

OMP — open source проект под лицензией MIT. Вот как внести свой вклад.

## Начало работы

1. Форкните репозиторий на GitHub
2. Клонируйте свой форк
3. Создайте ветку для изменений

```bash
git clone https://github.com/YOUR_USERNAME/oh-my-pi.git
cd oh-my-pi
git checkout -b feature/my-improvement
bun install
```

## Виды контрибьюций

### Баг-репорты
- Используйте GitHub Issues
- Укажите версию OMP, ОС, терминал
- Приложите логи из `~/.omp/logs/`

### Новые функции
- Обсудите идею в Issue или Discord
- Следуйте существующим паттернам кода

### Новые провайдеры
- Добавьте конфигурацию в `packages/ai/`
- Поддерживаемые API: openai-completions, anthropic-messages, google-generative-ai и др.

### Кастомные инструменты
- Создайте в `packages/coding-agent/src/tools/`

### Темы
- Добавьте JSON-файл в `packages/coding-agent/themes/`

### Документация
- Папка `docs/`

## Процесс Pull Request

1. Убедитесь что код собирается: `bun run build`
2. Проверьте тесты
3. Используйте conventional commits
4. Опишите изменения в PR

```bash
# Используйте OMP для коммитов!
omp commit --push
```

## Полезные ресурсы

- [DEVELOPMENT.md](https://github.com/can1357/oh-my-pi/blob/main/packages/coding-agent/DEVELOPMENT.md) — гайд по разработке
- [Discord](https://discord.gg/4NMW9cdXZa) — сообщество
- [CHANGELOG.md](https://github.com/can1357/oh-my-pi/blob/main/packages/coding-agent/CHANGELOG.md) — история изменений

## Лицензия

MIT. Copyright (c) 2025 Mario Zechner, 2025-2026 Can Bölük.

## Итоги

Контрибьюция в OMP приветствуется — от баг-репортов до новых функций. Используйте GitHub Issues и PR, следуя conventional commits.
