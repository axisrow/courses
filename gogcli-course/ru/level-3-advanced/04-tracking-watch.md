---
title: "Отслеживание и уведомления"
weight: 14
bookToc: true
---

# Отслеживание и уведомления

## Команда watch

Отслеживайте изменения в реальном времени:

```bash
gog mail watch                    # новые письма
gog mail watch --label INBOX      # только входящие
gog calendar watch                # изменения в календаре
gog drive watch --folder "Проекты"  # изменения в папке
```

## Фильтрация событий

```bash
gog mail watch --from boss@company.com
gog mail watch --subject "срочно"
gog calendar watch --calendar "Работа"
```

## Вывод в реальном времени

```bash
# Логирование в файл
gog mail watch --format json >> mail-log.jsonl

# Передача в другую программу
gog mail watch --format json | jq '.subject'
```

## Вебхуки

Для продвинутой интеграции можно настроить push-уведомления:

```bash
gog mail watch --webhook https://your-server.com/hook
gog drive watch --webhook https://your-server.com/drive-hook
```

## Комбинация с автоматизацией

```bash
# Автоответ на письма с определённой темой
gog mail watch --format json | while read -r msg; do
  subject=$(echo "$msg" | jq -r '.subject')
  from=$(echo "$msg" | jq -r '.from')
  if [[ "$subject" == *"статус"* ]]; then
    gog mail send --to "$from" --subject "Re: $subject" \
      --body "Всё работает нормально!"
  fi
done
```

## Практика

1. Запустите отслеживание входящей почты
2. Отправьте себе письмо и убедитесь, что watch его поймал
3. Напишите скрипт автоответа на письма с определённым ключевым словом
