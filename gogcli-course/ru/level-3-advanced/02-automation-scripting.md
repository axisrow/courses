---
title: "Автоматизация и скрипты"
weight: 12
bookToc: true
---

# Автоматизация и скрипты

## Основы скриптинга

gogcli отлично работает в shell-скриптах. Используйте `--format json` для машинной обработки.

### Простой скрипт: ежедневный отчёт

```bash
#!/bin/bash
# daily-report.sh — отправка сводки по почте

TODAY=$(date +%Y-%m-%d)
EVENTS=$(gog calendar list --date "$TODAY" --format text)
UNREAD=$(gog mail list --unread --max 5 --format text)

gog mail send \
  --to boss@company.com \
  --subject "Сводка за $TODAY" \
  --body "Встречи:\n$EVENTS\n\nНепрочитанные:\n$UNREAD"
```

## Работа с JSON и jq

```bash
# Получить ID всех непрочитанных писем
gog mail list --unread --format json | jq -r '.[].id'

# Подсчитать файлы на Диске
gog drive list --format json | jq 'length'
```

## Пакетная обработка

```bash
# Скачать все файлы из папки
for id in $(gog drive list --folder "Отчёты" --format json | jq -r '.[].id'); do
  gog drive download "$id" -o "./отчёты/"
done
```

## Cron-задания

```bash
# Каждый день в 9:00 — отправка отчёта
0 9 * * * /home/user/scripts/daily-report.sh
```

## Практика

1. Напишите скрипт, который архивирует прочитанные письма старше 30 дней
2. Настройте cron-задание для еженедельного бэкапа файлов с Диска
