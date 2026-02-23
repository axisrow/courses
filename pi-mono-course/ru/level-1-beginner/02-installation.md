---
title: "Установка Pi Mono"
weight: 2
bookToc: true
---

# Установка Pi Mono

## Введение

В этом уроке мы установим Pi Mono и подготовим рабочую среду.

## Требования

- **Node.js** версии 18 или выше
- **npm** (устанавливается вместе с Node.js)
- Терминал (командная строка)

## Пошаговая установка

### Шаг 1: Установите Node.js

Скачайте Node.js с [nodejs.org](https://nodejs.org) и установите его. Проверьте установку:

```bash
node --version
npm --version
```

### Шаг 2: Установите coding agent

```bash
npm install -g @mariozechner/pi-coding-agent
```

### Шаг 3: Настройте API-ключ

Для работы с AI-моделями нужен ключ. Например, для Anthropic:

```bash
export ANTHROPIC_API_KEY=sk-ant-ваш-ключ
```

Или используйте встроенную авторизацию:

```bash
pi
/login
```

### Шаг 4: Проверьте установку

```bash
pi --help
```

## Итоги

- Установили Node.js и npm
- Установили Pi coding agent глобально
- Настроили API-ключ для LLM-провайдера
