---
title: "Деплой DeerFlow"
weight: 4
bookToc: true
---

# Деплой DeerFlow

## Введение

В этом уроке мы рассмотрим, как развернуть DeerFlow в продакшн-среде: от Docker Compose до Kubernetes.

## Docker Compose (рекомендуется)

### Архитектура деплоя

```
Docker Compose
  ├─ nginx (порт 2026)      ← Обратный прокси
  ├─ web (порт 3000)        ← Frontend
  ├─ api (порт 8001)        ← Gateway API
  └─ langgraph (порт 2024)  ← LangGraph Server
```

### Шаги деплоя

#### 1. Подготовьте сервер

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install -y docker.io docker-compose-v2 git
sudo systemctl enable docker
```

#### 2. Клонируйте и настройте

```bash
git clone https://github.com/bytedance/deer-flow.git
cd deer-flow
make config
```

#### 3. Настройте переменные окружения

```bash
# .env
OPENAI_API_KEY=sk-your-key
# или другие провайдеры
```

#### 4. Настройте песочницу

Для продакшна используйте Docker-песочницу:

```yaml
# config.yaml
sandbox:
  use: src.community.aio_sandbox:AioSandboxProvider
```

#### 5. Инициализация и запуск

```bash
make docker-init    # Первый раз
make docker-start   # Запуск
```

#### 6. Проверьте работоспособность

```bash
curl http://localhost:2026/api/health
# Ожидаемый ответ: {"status": "ok"}
```

## Kubernetes

### С использованием Provisioner

Для масштабируемого деплоя с изолированными песочницами в подах Kubernetes:

```yaml
# config.yaml
sandbox:
  use: src.community.aio_sandbox:AioSandboxProvider
  provisioner_url: http://provisioner:8002
```

### Требования

- Docker Desktop с Kubernetes, OrbStack или аналогичный кластер
- Настроенный Provisioner (см. `docker/provisioner/README.md`)

## Обратный прокси

### Настройка Nginx (внешний)

Если вы хотите выставить DeerFlow в интернет:

```nginx
server {
    listen 443 ssl;
    server_name deerflow.example.com;

    ssl_certificate /etc/ssl/certs/cert.pem;
    ssl_certificate_key /etc/ssl/private/key.pem;

    location / {
        proxy_pass http://localhost:2026;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        # Для SSE (потоковый вывод)
        proxy_buffering off;
        proxy_cache off;
    }
}
```

> ⚠️ **Важно**: обязательно настройте аутентификацию перед открытием в интернет!

## Безопасность

### Чек-лист безопасности

- [ ] Используйте Docker-песочницу (не локальную)
- [ ] API-ключи только через переменные окружения
- [ ] HTTPS для внешнего доступа
- [ ] Аутентификация перед прокси
- [ ] Ограничьте сетевой доступ песочницы
- [ ] Регулярно обновляйте Docker-образы
- [ ] Мониторинг использования API-ключей

### Переменные окружения

Никогда не храните ключи в `config.yaml` для продакшна:

```yaml
# ✅ Правильно
api_key: $OPENAI_API_KEY

# ❌ Неправильно
api_key: sk-actual-key-here
```

## Мониторинг

### Логи

```bash
# Все сервисы
make docker-logs

# Конкретный сервис
docker compose logs -f api
docker compose logs -f langgraph
```

### Health Check

```bash
# Gateway API
curl http://localhost:8001/health

# Через Nginx
curl http://localhost:2026/api/health
```

## Обновление

```bash
git pull origin main
make docker-stop
make docker-init    # Если обновились образы
make docker-start
```

## Итоги

- Docker Compose — рекомендуемый способ деплоя
- Для продакшна используйте Docker-песочницу
- Настройте HTTPS и аутентификацию для внешнего доступа
- API-ключи — только через переменные окружения
- Kubernetes — для масштабируемых развёртываний
- Регулярно обновляйте и мониторьте систему
