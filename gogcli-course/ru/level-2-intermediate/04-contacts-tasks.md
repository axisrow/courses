---
title: "Контакты и Задачи"
weight: 9
bookToc: true
---

# Контакты и Задачи

## Контакты

### Поиск и просмотр

```bash
gog contacts search "Алиса" --max 10
gog contacts list --max 50
gog contacts get people/RESOURCE_NAME
gog contacts get alice@example.com
```

### Создание

```bash
gog contacts create \
  --given "Иван" \
  --family "Петров" \
  --email "ivan@example.com" \
  --phone "+79001234567"
```

### Обновление и удаление

```bash
gog contacts update people/RESOURCE_NAME \
  --given "Мария" \
  --email "maria@example.com" \
  --birthday "1990-05-12" \
  --notes "Познакомились на конференции"

gog contacts delete people/RESOURCE_NAME
```

### Другие контакты и справочник Workspace

```bash
gog contacts other list --max 50
gog contacts directory search "Мария" --max 10
```

## Задачи

### Списки задач

```bash
gog tasks lists
gog tasks lists create "Покупки"
```

### Работа с задачами

```bash
gog tasks list TASKLIST_ID --max 20
gog tasks add TASKLIST_ID --title "Купить продукты"
gog tasks add TASKLIST_ID --title "Оплатить счёт" --due 2025-04-01
gog tasks add TASKLIST_ID --title "Еженедельный обзор" \
  --due 2025-03-07 --repeat weekly --repeat-count 12
```

### Обновление

```bash
gog tasks update TASKLIST_ID TASK_ID --title "Купить органические продукты"
gog tasks done TASKLIST_ID TASK_ID      # Отметить выполненной
gog tasks undo TASKLIST_ID TASK_ID      # Отметить невыполненной
```

### Удаление

```bash
gog tasks delete TASKLIST_ID TASK_ID
gog tasks clear TASKLIST_ID    # Очистить все выполненные
```

## People API

```bash
gog people me                           # Ваш профиль
gog people search "Анна" --max 5       # Поиск в справочнике
gog people relations                    # Связи (руководитель и т.д.)
```

## Далее

В следующем уроке — Таблицы, Формы и Презентации.
