---
title: "Установка Shannon"
weight: 2
bookToc: true
---

# Установка Shannon

## Введение

В этом уроке мы установим всё необходимое для работы Shannon на вашем компьютере.

## Что понадобится

1. **Docker** — система контейнеризации (Shannon работает в контейнерах)
2. **API-ключ Anthropic** — Shannon использует Claude AI для анализа

## Шаг 1: Установка Docker

### macOS
Скачайте и установите [Docker Desktop](https://docs.docker.com/get-docker/). Всё работает «из коробки».

### Windows
Рекомендуется использовать **WSL2** (подсистема Linux для Windows):

```powershell
# Откройте PowerShell от администратора
wsl --install
wsl --set-default-version 2
wsl --install Ubuntu-24.04
```

Затем установите Docker Desktop и включите «Use the WSL 2 based engine» в настройках.

### Linux
Установите Docker по [официальной инструкции](https://docs.docker.com/get-docker/). Возможно, потребуется `sudo`.

## Шаг 2: Получение API-ключа

1. Перейдите на [console.anthropic.com](https://console.anthropic.com)
2. Зарегистрируйтесь или войдите в аккаунт
3. Создайте API-ключ
4. Сохраните его — он понадобится дальше

## Шаг 3: Клонирование Shannon

```bash
git clone https://github.com/KeygraphHQ/shannon.git
cd shannon
```

## Шаг 4: Настройка учётных данных

Создайте файл `.env` в папке Shannon:

```bash
cat > .env << 'EOF'
ANTHROPIC_API_KEY=ваш-ключ-сюда
CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
EOF
```

Или экспортируйте переменные:

```bash
export ANTHROPIC_API_KEY="ваш-ключ-сюда"
export CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
```

## Шаг 5: Проверка

Убедитесь, что Docker запущен:

```bash
docker --version
```

Если видите версию Docker — всё готово!

## Итоги

- Вы установили Docker
- Получили API-ключ Anthropic
- Клонировали репозиторий Shannon
- Настроили учётные данные

В следующем уроке мы запустим Shannon впервые.
