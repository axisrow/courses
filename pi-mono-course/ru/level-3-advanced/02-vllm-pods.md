---
title: "vLLM Pods"
weight: 2
bookToc: true
---

# vLLM Pods

## Введение

Пакет **pi-pods** позволяет развёртывать и управлять LLM на удалённых GPU-серверах с автоматической настройкой vLLM.

## Что делает pi-pods

- Настраивает vLLM на свежих Ubuntu-серверах
- Конфигурирует tool calling для агентных моделей
- Управляет несколькими моделями на одном сервере
- Предоставляет OpenAI-совместимые API для каждой модели

## Установка

```bash
npm install -g @mariozechner/pi
```

## Требования

- HuggingFace токен
- GPU-сервер с Ubuntu, SSH-доступом и NVIDIA драйверами

## Поддерживаемые провайдеры

- **DataCrunch** — NFS для общего хранения моделей
- **RunPod** — persistent storage
- **Vast.ai**, **AWS EC2** и любые Ubuntu-серверы с GPU

## Быстрый старт

```bash
export HF_TOKEN=ваш_токен
export PI_API_KEY=ваш_ключ

# Настроить pod
pi pods setup dc1 "ssh root@1.2.3.4" \
  --mount "sudo mount -t nfs nfs.server:/path /mnt/hf-models"

# Запустить модель
pi start Qwen/Qwen2.5-Coder-32B-Instruct --name qwen

# Интерактивный чат
pi agent qwen -i
```

## Итоги

- pi-pods автоматизирует развёртывание LLM на GPU
- Поддерживает DataCrunch, RunPod и другие провайдеры
- Предоставляет OpenAI-совместимый API
