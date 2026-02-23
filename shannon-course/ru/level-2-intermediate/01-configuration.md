---
title: "Конфигурация Shannon"
weight: 1
bookToc: true
---

# Конфигурация Shannon

## Введение

Shannon можно запустить без конфигурации, но для реальных приложений настройка необходима — например, чтобы Shannon мог войти в систему и протестировать защищённые страницы.

## Создание файла конфигурации

```bash
cp configs/example-config.yaml configs/my-app-config.yaml
```

Файлы конфигурации размещаются в папке `./configs/` — она автоматически монтируется в Docker-контейнер.

## Структура конфигурации

### Аутентификация

```yaml
authentication:
  login_type: form
  login_url: "https://your-app.com/login"
  credentials:
    username: "test@example.com"
    password: "yourpassword"
    totp_secret: "LB2E2RX7XFHSTGCK"  # Опционально, для 2FA

  login_flow:
    - "Type $username into the email field"
    - "Type $password into the password field"
    - "Click the 'Sign In' button"

  success_condition:
    type: url_contains
    value: "/dashboard"
```

**Что здесь происходит:**
- `login_type` — тип формы входа
- `credentials` — логин и пароль тестового аккаунта
- `totp_secret` — секрет для 2FA (если есть). Shannon автоматически генерирует TOTP-коды
- `login_flow` — пошаговые инструкции для AI, как войти в систему
- `success_condition` — как понять, что вход успешен

### Правила сканирования

```yaml
rules:
  avoid:
    - description: "Не тестировать выход из системы"
      type: path
      url_path: "/logout"

  focus:
    - description: "Сосредоточиться на API-эндпоинтах"
      type: path
      url_path: "/api"
```

- `avoid` — пути, которые Shannon должен игнорировать
- `focus` — пути, на которых нужно сосредоточиться

## Запуск с конфигурацией

```bash
./shannon start URL=https://your-app.com REPO=my-app CONFIG=./configs/my-app-config.yaml
```

## Примеры сценариев

### Простое приложение без авторизации
Конфигурация не нужна — просто запустите `./shannon start`.

### Приложение с логином
Добавьте секцию `authentication` с данными тестового аккаунта.

### Приложение с 2FA
Добавьте `totp_secret` в `credentials`. Shannon сам сгенерирует одноразовый код.

### Приложение с OAuth (Sign in with Google)
Shannon поддерживает продвинутые сценарии логина, включая OAuth-провайдеры.

## Итоги

- Конфигурация позволяет Shannon тестировать защищённые зоны приложения
- Файл YAML содержит данные для входа и правила сканирования
- Поддерживается 2FA/TOTP из коробки
- Правила `avoid` и `focus` управляют приоритетами сканирования
