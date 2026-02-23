---
title: "Spec-driven разработка"
level: 2
lesson: 1
language: ru
tags: [gsd, spec-driven, requirements]
---

# Spec-driven разработка

## Введение

GSD построен на принципе spec-driven development: сначала спецификация, потом код. Вместо «сделай мне сайт» вы получаете структурированные требования, дорожную карту и планы.

## Инструкции

### Структура спецификации

GSD автоматически создаёт:

1. **PROJECT.md** — высокоуровневое видение
2. **REQUIREMENTS.md** — конкретные требования, разделённые на v1/v2/out-of-scope
3. **ROADMAP.md** — фазы с привязкой к требованиям

### Как это работает

```
Ваша идея → Вопросы → Исследование → Требования → Дорожная карта → Планы → Код
```

Каждый шаг сужает неопределённость. К моменту написания кода AI точно знает что делать.

### Планы в XML

```xml
<task type="auto">
  <name>Создать эндпоинт логина</name>
  <files>src/api/auth/login.ts</files>
  <action>
    Использовать jose для JWT.
    Валидировать credentials.
    Вернуть httpOnly cookie.
  </action>
  <verify>curl POST /api/auth/login → 200 + cookie</verify>
  <done>Валидные credentials → cookie, невалидные → 401</done>
</task>
```

## Примеры

```
/gsd:new-project

> Я хочу SaaS для управления задачами с командами,
> канбан-доской и интеграцией со Slack.

GSD создаст:
- PROJECT.md с видением
- REQUIREMENTS.md с ~15-20 конкретных требований
- ROADMAP.md с 4-6 фазами
```

## Итоги

- Spec-driven = спецификация перед кодом
- GSD автоматически генерирует PROJECT, REQUIREMENTS, ROADMAP
- Каждый план — XML-структура с задачей и верификацией
- Неопределённость устраняется до написания кода
