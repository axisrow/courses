---
title: "Установка"
level: 1
lesson: 2
lang: ru
tags: [установка, bun, npm]
---

# Установка Oh My Pi

## Введение

Есть несколько способов установить OMP. Рекомендуемый — через Bun.

## Способ 1: Через Bun (рекомендуемый)

Требуется [Bun](https://bun.sh) версии >= 1.3.7.

```bash
# Установить Bun (если ещё нет)
curl -fsSL https://bun.sh/install | bash

# Установить OMP
bun install -g @oh-my-pi/pi-coding-agent
```

## Способ 2: Скрипт установки

**Linux / macOS:**

```bash
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh
```

**Windows (PowerShell):**

```powershell
irm https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.ps1 | iex
```

## Способ 3: Через mise

```bash
mise use -g github:can1357/oh-my-pi
```

## Способ 4: Скачать бинарник

Скачайте с [GitHub Releases](https://github.com/can1357/oh-my-pi/releases/latest).

## Проверка установки

```bash
omp --version
```

## Дополнительные опции установки

```bash
# Установка конкретной версии
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh -s -- --binary --ref v3.20.1

# Установка из исходников (ветка main)
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh -s -- --source --ref main
```

Путь установки можно задать через `PI_INSTALL_DIR`.

## Итоги

OMP можно установить через Bun, скрипт, mise или вручную. Рекомендуется Bun — быстро и просто.
