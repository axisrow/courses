---
title: "Slack Bot (Mom)"
weight: 5
bookToc: true
---

# Slack Bot (Mom)

## Введение

**Mom** (Master Of Mischief) — это Slack-бот на базе LLM, который может выполнять команды, работать с файлами и автоматизировать рабочие процессы. Mom сама устанавливает нужные инструменты и управляет своим окружением.

## Особенности

- **Самоуправляемость** — сама устанавливает инструменты и настраивает окружение
- **Bash-доступ** — выполняет любые команды
- **Docker-песочница** — безопасная изоляция
- **Рабочая память** — помнит контекст между сессиями
- **Создание CLI-утилит** — пишет собственные скрипты для повторяющихся задач

## Установка

```bash
npm install @mariozechner/pi-mom
```

## Настройка Slack

1. Создайте приложение на https://api.slack.com/apps
2. Включите **Socket Mode**
3. Добавьте Bot Token Scopes: `chat:write`, `channels:history`, `im:history` и др.
4. Подпишитесь на события: `app_mention`, `message.im`
5. Установите приложение в workspace

## Быстрый старт

```bash
export MOM_SLACK_APP_TOKEN=xapp-...
export MOM_SLACK_BOT_TOKEN=xoxb-...
export ANTHROPIC_API_KEY=sk-ant-...

# Docker-песочница (рекомендуется)
docker run -d --name mom-sandbox -v $(pwd)/data:/workspace alpine:latest tail -f /dev/null

# Запуск
mom --sandbox=docker:mom-sandbox ./data
```

## Итоги

- Mom — самоуправляемый Slack-бот на базе Pi
- Работает в Docker-песочнице для безопасности
- Сама создаёт инструменты для ваших задач
