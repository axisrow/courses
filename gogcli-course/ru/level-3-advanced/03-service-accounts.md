---
title: "Сервисные аккаунты"
weight: 13
bookToc: true
---

# Сервисные аккаунты

Сервисные аккаунты — это специальные аккаунты Google для автоматизации без участия пользователя.

## Когда нужен сервисный аккаунт

- Серверные скрипты без интерактивного входа
- Обработка данных организации (Google Workspace)
- CI/CD пайплайны

## Настройка

### 1. Создайте сервисный аккаунт в Google Cloud Console

Скачайте JSON-ключ и сохраните его в безопасном месте.

### 2. Авторизация в gogcli

```bash
gog auth service --key-file /path/to/service-key.json
gog auth service --key-file key.json --subject admin@company.com
```

Флаг `--subject` нужен для делегирования (impersonation) в Google Workspace.

### 3. Использование

```bash
gog --account service:my-service mail list
gog -a service:my-service drive list
```

## Делегирование полномочий

В Google Workspace администратор может разрешить сервисному аккаунту действовать от имени пользователей:

```bash
gog auth service --key-file key.json --subject user@company.com
gog mail list  # покажет почту user@company.com
```

## Безопасность

- Храните ключи в защищённом месте (не в git!)
- Используйте минимальные необходимые права (scopes)
- Регулярно ротируйте ключи

## Практика

1. Создайте сервисный аккаунт в Google Cloud Console
2. Авторизуйтесь через gogcli с JSON-ключом
3. Прочитайте список файлов на Диске через сервисный аккаунт
