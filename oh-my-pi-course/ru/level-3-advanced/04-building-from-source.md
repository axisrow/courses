---
title: "Сборка из исходников"
level: 3
lesson: 4
lang: ru
tags: [сборка, разработка, исходники, bun, rust]
---

# Сборка из исходников

## Введение

Если вы хотите модифицировать OMP или участвовать в разработке, вам нужно собрать проект из исходников.

## Требования

- [Bun](https://bun.sh) >= 1.3.7
- [Rust](https://rustup.rs/) (для нативных модулей)
- Git
- Node.js >= 18 (опционально, для совместимости)

## Клонирование

```bash
git clone https://github.com/can1357/oh-my-pi.git
cd oh-my-pi
```

## Установка зависимостей

```bash
bun install
```

## Сборка Rust-модулей

```bash
cd crates/pi-natives
cargo build --release
```

## Сборка TypeScript

```bash
bun run build
```

## Запуск локальной версии

```bash
bun run packages/coding-agent/src/cli.ts
```

## Установка через скрипт (source mode)

```bash
curl -fsSL https://raw.githubusercontent.com/can1357/oh-my-pi/main/scripts/install.sh | sh -s -- --source --ref main
```

## Структура проекта

```
oh-my-pi/
├── packages/
│   ├── ai/              # LLM-клиент
│   ├── agent/           # Рантайм агента
│   ├── coding-agent/    # CLI + SDK
│   ├── tui/             # Терминальный UI
│   ├── natives/         # N-API биндинги
│   ├── stats/           # Дашборд статистики
│   └── utils/           # Утилиты
├── crates/
│   ├── pi-natives/      # Rust N-API
│   ├── brush-core-vendored/
│   └── brush-builtins-vendored/
├── scripts/             # Скрипты установки
└── docs/                # Документация
```

## Отладка

В OMP используйте `/debug` для инструментов отладки и профилирования.

Логи пишутся в `~/.omp/logs/` с ежедневной ротацией.

## Итоги

Сборка OMP требует Bun и Rust. Монорепо организовано в packages/ (TypeScript) и crates/ (Rust).
