---
title: "Несколько аккаунтов и алиасы"
weight: 11
bookToc: true
---

# Несколько аккаунтов и алиасы

## Добавление аккаунтов

```bash
gog auth add personal@gmail.com
gog auth add work@company.com
```

## Переключение между аккаунтами

### Для одной команды

```bash
gog --account work@company.com mail list
gog -a personal@gmail.com drive list
```

### Установка аккаунта по умолчанию

```bash
gog auth default work@company.com
gog auth list   # покажет все аккаунты и текущий
```

## Алиасы

Создавайте короткие имена для аккаунтов:

```bash
gog auth alias work work@company.com
gog auth alias home personal@gmail.com
```

Теперь можно писать короче:

```bash
gog -a work mail list
gog -a home drive list
```

## Конфигурация для каждого аккаунта

```bash
gog config set --account work default_format json
gog config set --account home default_format table
```

## Практика

1. Добавьте два аккаунта Google
2. Создайте алиасы для них
3. Отправьте письмо с рабочего аккаунта на личный
