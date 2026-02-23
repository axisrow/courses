---
title: "Первые команды"
weight: 4
bookToc: true
---

# Первые команды

Аутентификация настроена — давайте попробуем реальные команды.

## Установите аккаунт по умолчанию

```bash
export GOG_ACCOUNT=you@gmail.com
```

Добавьте эту строку в `~/.bashrc` или `~/.zshrc`, чтобы сделать её постоянной.

## Gmail: проверка почты

```bash
# Список ярлыков
gog gmail labels list

# Письма за последние 7 дней
gog gmail search 'newer_than:7d' --max 5

# Прочитать конкретную цепочку писем
gog gmail thread get THREAD_ID
```

## Календарь: расписание

```bash
# Список календарей
gog calendar calendars

# События на сегодня
gog calendar events primary --today

# События на эту неделю
gog calendar events primary --week
```

## Диск: файлы

```bash
# Последние файлы
gog drive ls --max 10

# Поиск файла
gog drive search "бюджет" --max 5
```

## Контакты

```bash
gog contacts search "Иван" --max 5
```

## Задачи

```bash
# Списки задач
gog tasks lists

# Задачи в списке
gog tasks list TASKLIST_ID
```

## Краткая справка

| Что нужно | Команда |
|-----------|---------|
| Недавние письма | `gog gmail search 'newer_than:7d'` |
| Сегодняшние события | `gog calendar events primary --today` |
| Список файлов | `gog drive ls --max 10` |
| Найти контакт | `gog contacts search "имя"` |
| Списки задач | `gog tasks lists` |
| Текущее время | `gog time now` |

## Советы

- Добавляйте `--max N` для ограничения результатов
- Используйте `--account email` для указания аккаунта
- У каждой команды есть `--help`

## Далее

В следующем уроке вы узнаете о форматах вывода — таблица, текст и JSON.
