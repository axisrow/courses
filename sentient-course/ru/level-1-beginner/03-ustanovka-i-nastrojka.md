---
title: "Установка и настройка"
weight: 3
bookToc: true
---

# Установка и настройка

## Что понадобится

- Компьютер с **Windows, macOS или Linux**.
- Установленный **Docker** (проще всего Docker Desktop).
- **Node.js** версии 18+ для клиента.
- **Python 3.11+** для сервера.
- **Git** для клонирования репозитория.

## Шаг 1 — Клонирование

```bash
git clone https://github.com/existence-master/Sentient.git
cd Sentient
```

## Шаг 2 — Переменные окружения

```bash
cp src/server/.env.template src/server/.env
cp src/client/.env.template src/client/.env
```

Откройте каждый `.env` файл и заполните необходимые значения (API-ключи, адреса баз данных и т. д.).

## Шаг 3 — Запуск баз данных

```bash
docker compose -f start_pgvector.yaml up -d
docker compose -f start_redis.yaml up -d
docker compose -f start_chroma.yaml up -d
docker compose -f start_litellm.yaml up -d
```

## Шаг 4 — Запуск сервера

```bash
cd src/server
pip install -r requirements.txt
python -m uvicorn main.app:app --reload
```

## Шаг 5 — Запуск клиента

```bash
cd src/client
npm install
npm run dev
```

Откройте `http://localhost:3000` в браузере.

## Docker Compose (всё в одном)

```bash
docker compose -f src/docker-compose.selfhost.yml up -d
```

## Итог

Sentient запущен локально. В следующем уроке вы проведёте первый диалог.
