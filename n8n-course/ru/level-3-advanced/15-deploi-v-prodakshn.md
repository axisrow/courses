---
title: "Деплой в продакшн"
weight: 15
bookToc: true
---

# Деплой в продакшн

## Продакшн vs Разработка

| Аспект | Разработка | Продакшн |
|--------|-----------|----------|
| БД | SQLite | PostgreSQL |
| Процесс | Ручной | Docker / PM2 |
| URL | localhost | Домен + HTTPS |
| Бэкапы | Нет | Автоматические |

## Docker Compose

```yaml
version: '3.8'
services:
  n8n:
    image: docker.n8n.io/n8nio/n8n
    restart: always
    ports:
      - "5678:5678"
    environment:
      - DB_TYPE=postgresdb
      - DB_POSTGRESDB_HOST=postgres
      - DB_POSTGRESDB_DATABASE=n8n
      - DB_POSTGRESDB_USER=n8n
      - DB_POSTGRESDB_PASSWORD=${DB_PASSWORD}
      - N8N_ENCRYPTION_KEY=${ENCRYPTION_KEY}
      - WEBHOOK_URL=https://n8n.yourdomain.com/
      - EXECUTIONS_MODE=queue
      - QUEUE_BULL_REDIS_HOST=redis
    volumes:
      - n8n_data:/home/node/.n8n
    depends_on:
      - postgres
      - redis

  postgres:
    image: postgres:15
    restart: always
    environment:
      - POSTGRES_DB=n8n
      - POSTGRES_USER=n8n
      - POSTGRES_PASSWORD=${DB_PASSWORD}
    volumes:
      - postgres_data:/var/lib/postgresql/data

  redis:
    image: redis:7
    restart: always

  n8n-worker:
    image: docker.n8n.io/n8nio/n8n
    command: worker
    restart: always
    environment:
      - DB_TYPE=postgresdb
      - DB_POSTGRESDB_HOST=postgres
      - DB_POSTGRESDB_DATABASE=n8n
      - DB_POSTGRESDB_USER=n8n
      - DB_POSTGRESDB_PASSWORD=${DB_PASSWORD}
      - N8N_ENCRYPTION_KEY=${ENCRYPTION_KEY}
      - EXECUTIONS_MODE=queue
      - QUEUE_BULL_REDIS_HOST=redis
    depends_on:
      - redis

volumes:
  n8n_data:
  postgres_data:
```

## Переменные окружения (.env)

```bash
DB_PASSWORD=надёжный_пароль
ENCRYPTION_KEY=случайная_строка_32_символа
WEBHOOK_URL=https://n8n.yourdomain.com/
```

## Бэкапы

### База данных
```bash
pg_dump -U n8n n8n > backup_$(date +%Y%m%d).sql
```

### Экспорт workflow
```bash
n8n export:workflow --all --output=workflows/
n8n export:credentials --all --output=credentials/
```

## Чеклист запуска

- [ ] PostgreSQL настроен
- [ ] HTTPS с валидным сертификатом
- [ ] Encryption key установлен и сохранён
- [ ] Учётные данные защищены
- [ ] Error workflow активен
- [ ] Бэкапы автоматизированы
- [ ] Мониторинг настроен
- [ ] Публичный доступ ограничен
- [ ] Автоудаление старых выполнений

## Обновление

1. Протестируйте на staging
2. Сделайте бэкап
3. `docker compose pull`
4. `docker compose up -d`
5. Проверьте все workflow

## Итог

Поздравляем! Вы завершили курс по n8n. Вы умеете создавать, оптимизировать, защищать и деплоить workflow. Автоматизируйте всё!
