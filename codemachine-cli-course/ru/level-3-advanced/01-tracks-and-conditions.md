---
title: "Треки и условия"
weight: 1
bookToc: true
---

# Треки и условия

## Что такое треки?

Треки позволяют пользователям выбрать тип проекта при запуске workflow:

```javascript
tracks: {
  question: 'Какой тип веб-приложения?',
  options: {
    spa: { label: 'SPA', description: 'React/Vue/Angular' },
    ssr: { label: 'SSR', description: 'Next.js/Nuxt.js' },
    static: { label: 'Статический сайт', description: 'HTML/CSS/JS' },
  },
},
steps: [
  resolveStep('researcher'),
  resolveStep('spa-setup', { tracks: ['spa'] }),
  resolveStep('ssr-setup', { tracks: ['ssr'] }),
  resolveStep('deployment'),
],
```

## Группы условий

Условия — как переключатели фич:

```javascript
conditionGroups: [
  {
    id: 'features',
    question: 'Какие фичи нужны?',
    multiSelect: true,
    conditions: {
      auth: { label: 'Аутентификация' },
      payments: { label: 'Платежи' },
      notifications: { label: 'Уведомления' },
    },
  },
],
```

## Вложенные условия

```javascript
children: {
  auth: {
    question: 'Какой метод авторизации?',
    multiSelect: false,
    conditions: {
      oauth: { label: 'OAuth (Google/GitHub)' },
      email: { label: 'Email/Пароль' },
    },
  },
},
```

## Комбинация треков и условий

```javascript
conditionGroups: [
  {
    id: 'database',
    question: 'Какая база данных?',
    tracks: ['spa', 'ssr'],  // Только для SPA и SSR
    conditions: {
      postgres: { label: 'PostgreSQL' },
      mongodb: { label: 'MongoDB' },
    },
  },
],
```

## Итог

- Треки для выбора типа проекта
- Условия как переключатели фич
- Вложенные условия для уточняющих вопросов
- Шаги фильтруются по трекам и условиям

> **Следующий урок:** Инженерия контекста.
