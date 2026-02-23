---
title: "Создание кастомных атак"
weight: 2
bookToc: true
---

# Создание кастомных атак

## Введение

Shannon использует AI-агентов для атак, поэтому «кастомные атаки» означают управление поведением этих агентов через конфигурацию и промпты.

## Управление через конфигурацию

### Фокус на определённых путях

```yaml
rules:
  focus:
    - description: "Тестировать только API v2"
      type: path
      url_path: "/api/v2"
    - description: "Особое внимание на загрузку файлов"
      type: path
      url_path: "/upload"
```

### Исключение путей

```yaml
rules:
  avoid:
    - description: "Не трогать платёжную систему"
      type: path
      url_path: "/payment"
    - description: "Не трогать выход"
      type: path
      url_path: "/logout"
```

## Кастомные login-flow

Для сложных сценариев входа опишите каждый шаг:

```yaml
authentication:
  login_flow:
    - "Navigate to the login page"
    - "Click 'Sign in with SSO'"
    - "Type $username into the corporate email field"
    - "Click 'Next'"
    - "Type $password into the password field"
    - "Type the TOTP code into the verification field"
    - "Click 'Verify'"
    - "Wait for redirect to dashboard"
```

AI-агент интерпретирует эти инструкции и выполняет их в браузере.

## Тестирование нескольких ролей

Создайте отдельные конфигурации для разных ролей:

```bash
# Тест от имени обычного пользователя
./shannon start URL=https://app.com REPO=app CONFIG=./configs/user-config.yaml

# Тест от имени администратора
./shannon start URL=https://app.com REPO=app CONFIG=./configs/admin-config.yaml
```

Сравнив результаты, вы увидите, какие функции администратора доступны обычному пользователю (эскалация привилегий).

## Продвинутые сценарии

### Мульти-репозиторий

Для микросервисной архитектуры объедините все репозитории:

```bash
mkdir ./repos/platform
cd ./repos/platform
git clone frontend-repo
git clone auth-service-repo
git clone api-gateway-repo
```

### Кастомный выходной каталог

```bash
./shannon start URL=https://app.com REPO=app OUTPUT=./reports/q1-2025
```

## Ограничения

Shannon Lite не позволяет:
- Добавлять новые категории уязвимостей
- Создавать собственные агенты
- Модифицировать промпты агентов (без изменения исходного кода)

Для этого нужно изменять исходный код Shannon (лицензия AGPL позволяет для внутреннего использования).

## Итоги

- Кастомные атаки управляются через YAML-конфигурацию
- Можно фокусировать и исключать определённые пути
- Сложные login-flow описываются на естественном языке
- Тестирование разных ролей выявляет проблемы авторизации
