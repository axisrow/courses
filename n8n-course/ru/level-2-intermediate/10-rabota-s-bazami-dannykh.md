---
title: "Работа с базами данных"
weight: 10
bookToc: true
---

# Работа с базами данных

## Поддерживаемые БД

| База данных | Нод |
|------------|-----|
| PostgreSQL | Postgres |
| MySQL | MySQL |
| MongoDB | MongoDB |
| SQLite | SQLite |
| Microsoft SQL | Microsoft SQL |
| Redis | Redis |

## Подключение

1. Добавьте нод базы данных (например, **Postgres**)
2. **Create New Credential**
3. Заполните: хост, порт, имя БД, пользователь, пароль
4. **Test Connection**
5. Сохраните

## Основные операции

### Чтение (Select)
```sql
SELECT * FROM customers WHERE country = 'RU' LIMIT 10
```
Каждая строка → один элемент в n8n.

### Вставка (Insert)
- Операция: **Insert**
- Таблица: `customers`
- Сопоставьте поля n8n с колонками таблицы

### Обновление (Update)
- Операция: **Update**
- Ключ: колонка для сопоставления (например, `id`)
- Колонки для обновления

### Удаление (Delete)
- Операция: **Delete**
- Условие: какие строки удалить

## Произвольный SQL

```sql
SELECT c.name, COUNT(o.id) as order_count
FROM customers c
LEFT JOIN orders o ON c.id = o.customer_id
GROUP BY c.name
HAVING COUNT(o.id) > 5
```

## Лучшие практики

1. Используйте систему учётных данных
2. Параметризуйте запросы (защита от SQL-инъекций)
3. Всегда ставьте LIMIT
4. Тестируйте на малых данных
5. Используйте транзакции для связанных операций

## Пример: синхронизация API → БД

```
Schedule Trigger (ежедневно)
  → HTTP Request (данные из API)
  → Set (маппинг полей)
  → Postgres (upsert в БД)
```

## Практика

1. Настройте БД (SQLite или Postgres)
2. Создайте таблицу: `id`, `name`, `email`, `created_at`
3. Workflow для вставки 3 записей
4. Workflow для чтения и фильтрации

## Итог

Вы умеете работать с базами данных. Средний уровень завершён! Далее — пользовательские функции.
