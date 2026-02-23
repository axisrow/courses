# Урок 5. Запуск на сервере (24/7)

## Зачем это нужно

Если OpenClaw работает на вашем ноутбуке, он выключается, когда вы закрываете крышку. Чтобы ассистент был доступен круглосуточно, его нужно запустить на **сервере** — компьютере, который работает постоянно. Это может быть арендованный сервер в облаке за $5/месяц.

## Варианты запуска

| Вариант | Сложность | Цена | Для кого |
|---------|-----------|------|----------|
| **Hetzner VPS + Docker** | Средняя | ~$5/мес | Самый популярный вариант |
| **Fly.io** | Низкая | ~$5/мес | Быстрый старт без SSH |
| **Любой VPS** | Средняя | $3-10/мес | DigitalOcean, Oracle и др. |
| **Домашний сервер** | Высокая | $0 | Raspberry Pi, старый ПК |

## Вариант 1: Hetzner VPS + Docker (рекомендуемый)

### Что нужно
- Аккаунт на [hetzner.com](https://hetzner.com)
- Базовое знакомство с терминалом
- ~20 минут

### Шаг 1. Арендуйте сервер

На Hetzner выберите самый дешёвый VPS с Ubuntu или Debian. Подойдёт минимальная конфигурация.

### Шаг 2. Подключитесь по SSH

**SSH** (Secure Shell) — это способ удалённо управлять сервером через терминал.

```bash
ssh root@ваш-ip-адрес
```

### Шаг 3. Установите Docker

**Docker** — это программа для запуска приложений в изолированных контейнерах.

```bash
apt update && apt install -y docker.io docker-compose-v2
```

### Шаг 4. Скачайте OpenClaw

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
```

### Шаг 5. Запустите настройку

```bash
./docker-setup.sh
```

Скрипт автоматически:
- Соберёт образ Docker
- Запустит мастер начальной настройки
- Создаст токен для безопасного доступа
- Запустит Gateway

### Шаг 6. Проверьте работу

```bash
docker compose exec openclaw-gateway node dist/index.js health --token "$OPENCLAW_GATEWAY_TOKEN"
```

### Шаг 7. Доступ из браузера

Создайте SSH-туннель с вашего ноутбука:

```bash
ssh -N -L 18789:127.0.0.1:18789 root@ваш-ip-адрес
```

Теперь откройте `http://127.0.0.1:18789/` в браузере — вы увидите панель управления.

## Вариант 2: Fly.io

**Fly.io** — это облачная платформа, которая упрощает развёртывание. Не нужно настраивать сервер вручную.

### Шаг 1. Установите flyctl

```bash
curl -L https://fly.io/install.sh | sh
```

### Шаг 2. Создайте приложение

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw

fly apps create my-openclaw
fly volumes create openclaw_data --size 1 --region iad
```

### Шаг 3. Настройте секреты

```bash
fly secrets set ANTHROPIC_API_KEY=ваш-ключ
fly secrets set OPENCLAW_GATEWAY_TOKEN=ваш-токен
fly secrets set TELEGRAM_BOT_TOKEN=ваш-токен-бота
```

### Шаг 4. Разверните

```bash
fly deploy
```

Fly.io автоматически:
- Соберёт образ
- Развернёт его на сервере
- Настроит HTTPS
- Перезапустит при сбоях

## Вариант 3: Любой VPS с Docker

Общий порядок для любого VPS-провайдера (DigitalOcean, Oracle, Vultr и т.д.):

1. Арендуйте сервер с Ubuntu/Debian
2. Установите Docker
3. Клонируйте репозиторий OpenClaw
4. Запустите `./docker-setup.sh`
5. Настройте автоперезапуск (Docker Compose делает это автоматически)

## Важные настройки для сервера

### Хранение данных

Все данные OpenClaw хранятся в `~/.openclaw/`. Убедитесь, что эта папка на постоянном диске (не во временной памяти).

При использовании Docker данные монтируются с хоста:

```yaml
volumes:
  - ~/.openclaw:/home/node/.openclaw
  - ~/.openclaw/workspace:/home/node/.openclaw/workspace
```

### Настройка каналов в Docker

```bash
# WhatsApp (QR-код)
docker compose run --rm openclaw-cli channels login

# Telegram
docker compose run --rm openclaw-cli channels add --channel telegram --token "ваш-токен"

# Discord
docker compose run --rm openclaw-cli channels add --channel discord --token "ваш-токен"
```

### Права доступа

Docker-образ OpenClaw работает от пользователя `node` (uid 1000). Если видите ошибки доступа:

```bash
sudo chown -R 1000:1000 ~/.openclaw
```

### Дополнительные пакеты

Если нужны системные программы внутри контейнера:

```bash
export OPENCLAW_DOCKER_APT_PACKAGES="ffmpeg git curl"
./docker-setup.sh
```

## Автоматический перезапуск

Docker Compose перезапускает контейнер автоматически при сбое. Чтобы запускался при загрузке сервера:

```bash
systemctl enable docker
```

Для проверки:

```bash
docker compose ps
docker compose logs --tail 50
```

## Итоги урока

- Для работы 24/7 запустите OpenClaw на **сервере** (VPS)
- **Hetzner + Docker** — самый популярный и дешёвый вариант (~$5/мес)
- **Fly.io** — самый простой вариант без настройки сервера
- Используйте `./docker-setup.sh` для автоматической настройки
- Данные хранятся в `~/.openclaw/` — не забывайте про резервные копии
- SSH-туннель позволяет безопасно управлять сервером из браузера
