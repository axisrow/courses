---
title: "Интеграция через API"
weight: 2
bookToc: true
---

# Интеграция через API

## API Dify

Каждое опубликованное приложение предоставляет REST API. Это позволяет встроить AI в ваши продукты.

## Аутентификация

Все запросы требуют API-ключ в заголовке:

```
Authorization: Bearer app-xxxxxxxxxxxx
```

Ключ находится в **Студия → ваше приложение → Доступ к API**.

## Chat API

### Отправка сообщения

```bash
curl -X POST 'https://api.dify.ai/v1/chat-messages' \
  -H 'Authorization: Bearer app-xxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "inputs": {},
    "query": "Что такое Dify?",
    "user": "user-123",
    "conversation_id": ""
  }'
```

### Потоковый ответ

Добавьте `"response_mode": "streaming"` для получения Server-Sent Events:

```json
{
  "query": "Расскажи о Dify",
  "response_mode": "streaming",
  "user": "user-123"
}
```

## API генерации текста

```bash
curl -X POST 'https://api.dify.ai/v1/completion-messages' \
  -H 'Authorization: Bearer app-xxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "inputs": {"topic": "Тренды AI"},
    "user": "user-123"
  }'
```

## Основные эндпоинты

| Эндпоинт | Назначение |
|----------|-----------|
| `POST /chat-messages` | Отправить сообщение в чат |
| `GET /conversations` | Список разговоров |
| `GET /messages` | История сообщений |
| `POST /completion-messages` | Генерация текста |
| `POST /files/upload` | Загрузка файлов |

## Лимиты

В облачной версии лимиты зависят от плана. В self-hosted лимитов нет по умолчанию, но стоит добавить свои.

## Следующий шаг

Давайте создадим сложную логику с помощью воркфлоу!
