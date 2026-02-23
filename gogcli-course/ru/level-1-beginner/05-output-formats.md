---
title: "Форматы вывода"
weight: 5
bookToc: true
---

# Форматы вывода

gogcli поддерживает три формата вывода данных.

## 1. По умолчанию: таблица с цветами

```bash
gog gmail search 'newer_than:7d' --max 3
```

Лучше всего для: **чтения в терминале**.

## 2. Простой текст (TSV)

Добавьте `--plain` для вывода с разделителями-табуляциями без цветов:

```bash
gog gmail search 'newer_than:7d' --max 3 --plain
```

Лучше для: **передачи в другие программы** (grep, awk, cut).

```bash
gog gmail search 'newer_than:30d' --plain | grep "alice@"
```

## 3. JSON

Добавьте `--json` для машиночитаемого формата:

```bash
gog gmail search 'newer_than:7d' --max 3 --json
```

Лучше для: **скриптов и автоматизации**.

### Работа с JSON через jq

```bash
# Получить только ID цепочек
gog gmail search 'newer_than:7d' --json | jq -r '.threads[].id'

# Найти PDF-файлы на Диске
gog drive ls --json | jq '.files[] | select(.mimeType=="application/pdf")'
```

## Формат по умолчанию

```bash
export GOG_JSON=1     # Всегда JSON
export GOG_PLAIN=1    # Всегда простой текст
```

## Управление цветом

```bash
gog --color never gmail search 'newer_than:7d'    # Без цветов
gog --color always gmail search 'newer_than:7d'   # Всегда с цветами
```

## Важно: stdout и stderr

Данные идут в stdout, прогресс и подсказки — в stderr. Перенаправление работает чисто:

```bash
gog gmail search 'newer_than:7d' --json > emails.json
```

## Итого

| Флаг | Формат | Когда использовать |
|------|--------|-------------------|
| *(нет)* | Цветная таблица | Чтение в терминале |
| `--plain` | С табуляциями | Передача в grep/awk |
| `--json` | JSON | Скрипты, автоматизация |

## Далее

Вы завершили уровень «Начинающий»! Переходите к **Уровню 2: Средний**, чтобы изучить каждый сервис Google подробно.
