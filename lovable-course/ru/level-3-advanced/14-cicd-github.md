---
title: "CI/CD и GitHub"
weight: 14
bookToc: true
---

# CI/CD и GitHub

Подключите проект к GitHub и автоматизируйте деплой.

## Экспорт на GitHub

1. Нажмите **Export to GitHub**.
2. Lovable создаст репозиторий с кодом.
3. Каждое изменение синхронизируется автоматически.

## Синхронизация

- Lovable пушит коммиты при каждом изменении.
- Можно клонировать и работать локально.
- Пуш обратно — Lovable подхватит изменения.

## Локальная разработка

```bash
git clone https://github.com/your-user/your-app.git
cd your-app
npm install
npm run dev
```

## CI/CD с Vercel

1. Подключите GitHub-репо к [Vercel](https://vercel.com).
2. Vercel деплоит автоматически при каждом пуше.
3. Preview-деплой для pull request'ов.

## CI/CD с Netlify

1. Подключите репо к [Netlify](https://netlify.com).
2. Команда сборки: `npm run build`.
3. Директория: `dist`.

## GitHub Actions

```yaml
name: Build
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm install
      - run: npm run build
```

## Стратегия веток

| Ветка | Назначение |
|-------|-----------|
| main | Продакшн |
| develop | Интеграция |
| feature/* | Новые фичи |

## Итог

Экспортируйте на GitHub. Деплойте через Vercel или Netlify. Автоматизируйте с GitHub Actions.
