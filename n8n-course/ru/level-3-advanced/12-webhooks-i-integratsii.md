---
title: "Вебхуки и интеграции"
weight: 12
bookToc: true
---

# Вебхуки и интеграции

## Что такое вебхуки?

Вебхуки — «обратные API». Вместо того чтобы вы запрашивали данные, сервис сам отправляет их вам при наступлении события.

## Настройка вебхука в n8n

1. Добавьте нод **Webhook** как триггер
2. Выберите HTTP-метод (GET или POST)
3. Скопируйте **Webhook URL** (тестовый и продакшн)
4. Тестовый URL — для разработки, продакшн — для активного workflow

### Настройки
- **Path** — путь URL (например, `/form-submit`)
- **Authentication** — None, Basic Auth, Header Auth
- **Response Mode** — ответить сразу или после обработки

## Получение данных

- `{{ $json.body }}` — тело запроса
- `{{ $json.headers }}` — заголовки
- `{{ $json.query }}` — параметры URL

## Ответ на вебхук

Нод **Respond to Webhook** позволяет отправить свой ответ:
```json
{
  "status": "success",
  "message": "Данные получены",
  "id": "{{ $json.id }}"
}
```

## Примеры интеграций

### GitHub → Slack
```
Webhook (события GitHub)
  → IF (тип = "push")
  → Set (форматирование)
  → Slack (#dev канал)
```

### Stripe → База данных
```
Webhook (платежи Stripe)
  → IF (событие = "payment_intent.succeeded")
  → Set (сумма, клиент)
  → Postgres (запись платежа)
```

### Форма → Email + Таблица
```
Webhook (данные формы)
  → Google Sheets (сохранить)
  → Gmail (подтверждение)
```

## Простой API на n8n

```
GET /api/users  → Webhook → Postgres (SELECT) → Respond to Webhook
POST /api/users → Webhook → Postgres (INSERT) → Respond to Webhook
```

## Безопасность

- Используйте аутентификацию на вебхуках
- Валидируйте входящие данные
- Используйте HTTPS
- Проверяйте подписи (Stripe, GitHub)

## Практика

1. Создайте вебхук для POST-данных
2. Проверьте наличие полей `name` и `email`
3. Сохраните в Google Sheet
4. Верните ответ с ID

## Итог

Вы умеете строить интеграции на вебхуках. Далее — производительность и масштабирование.
