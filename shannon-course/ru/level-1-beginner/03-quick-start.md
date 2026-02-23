---
title: "Быстрый старт"
weight: 3
bookToc: true
---

# Быстрый старт

## Введение

Теперь, когда всё установлено, давайте запустим Shannon и познакомимся с основными командами.

## Подготовка репозитория для анализа

Shannon анализирует исходный код вашего приложения. Нужно поместить его в папку `./repos/`:

```bash
# Клонируйте ваш проект в папку repos
git clone https://github.com/your-org/your-app.git ./repos/your-app
```

Для приложений с несколькими репозиториями (фронтенд + бэкенд):

```bash
mkdir ./repos/my-app
cd ./repos/my-app
git clone https://github.com/your-org/frontend.git
git clone https://github.com/your-org/backend.git
```

## Запуск пентеста

Одна команда — и Shannon начинает работу:

```bash
./shannon start URL=https://your-app.com REPO=your-app
```

- `URL` — адрес работающего приложения
- `REPO` — имя папки в `./repos/`

Shannon соберёт контейнеры, запустит workflow и вернёт ID сессии. Тест работает в фоновом режиме.

## Мониторинг прогресса

```bash
# Просмотр логов в реальном времени
./shannon logs

# Запрос статуса конкретного workflow
./shannon query ID=shannon-1234567890

# Веб-интерфейс Temporal для детального мониторинга
open http://localhost:8233
```

## Остановка Shannon

```bash
# Остановить контейнеры (данные сохраняются)
./shannon stop

# Полная очистка (удалить все данные)
./shannon stop CLEAN=true
```

## Тестирование локальных приложений

Docker-контейнеры не видят `localhost` вашей машины. Используйте специальный адрес:

```bash
./shannon start URL=http://host.docker.internal:3000 REPO=my-app
```

## Итоги

- Вы научились подготавливать репозиторий для анализа
- Узнали основную команду запуска `./shannon start`
- Можете отслеживать прогресс через логи и веб-интерфейс
- Знаете, как тестировать локальные приложения
