---
title: "Мастерство работы с Календарём"
weight: 7
bookToc: true
---

# Мастерство работы с Календарём

Управляйте расписанием полностью из терминала.

## Просмотр событий

```bash
gog calendar events primary --today        # Сегодня
gog calendar events primary --tomorrow     # Завтра
gog calendar events primary --week         # Эта неделя
gog calendar events primary --days 3       # Следующие 3 дня
gog calendar events primary --from 2025-03-01 --to 2025-03-15  # Диапазон дат
gog calendar events --all --today          # Все календари сразу
```

## Поиск событий

```bash
gog calendar search "встреча" --today
gog calendar search "день рождения" --days 365
```

## Создание событий

```bash
# Простое событие
gog calendar create primary \
  --summary "Обед с Алисой" \
  --from 2025-03-15T12:00:00Z \
  --to 2025-03-15T13:00:00Z

# С участниками и местом
gog calendar create primary \
  --summary "Синхронизация команды" \
  --from 2025-03-15T14:00:00Z \
  --to 2025-03-15T15:00:00Z \
  --attendees "alice@example.com,bob@example.com" \
  --location "Переговорная Б"

# Повторяющееся событие с напоминаниями
gog calendar create primary \
  --summary "Еженедельный отчёт" \
  --from 2025-03-17T09:00:00Z \
  --to 2025-03-17T09:30:00Z \
  --rrule "RRULE:FREQ=WEEKLY;BYDAY=MO" \
  --reminder "popup:15m" \
  --reminder "email:1h"

# Событие на весь день
gog calendar create primary \
  --summary "Выходной" \
  --from 2025-12-25 --to 2025-12-26 --all-day
```

## Обновление и удаление

```bash
gog calendar update primary EVENT_ID --summary "Переименованная встреча"
gog calendar update primary EVENT_ID --add-attendee "charlie@example.com"
gog calendar delete primary EVENT_ID
```

## Ответ на приглашения

```bash
gog calendar respond primary EVENT_ID --status accepted
gog calendar respond primary EVENT_ID --status declined
gog calendar respond primary EVENT_ID --status tentative
```

## Проверка доступности

```bash
gog calendar freebusy --calendars "primary,colleague@example.com" \
  --from 2025-03-15T00:00:00Z --to 2025-03-16T00:00:00Z

gog calendar conflicts --calendars "primary" --today
```

## Специальные типы событий

```bash
gog calendar focus-time --from 2025-03-15T13:00:00Z --to 2025-03-15T15:00:00Z
gog calendar out-of-office --from 2025-04-01 --to 2025-04-02 --all-day
gog calendar working-location --type office --office-label "Главный офис" \
  --from 2025-03-17 --to 2025-03-18
```

## Часовые пояса

```bash
export GOG_TIMEZONE=Europe/Moscow
gog calendar events primary --today
```

## Далее

В следующем уроке — работа с файлами через Google Диск.
