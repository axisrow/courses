---
title: "Сложные навыки со скриптами"
weight: 2
bookToc: true
---

# Сложные навыки со скриптами

## Введение

Простые навыки содержат только текстовые инструкции. Но для задач, требующих точности и повторяемости, навыки могут включать скрипты — исполняемый код на Python, Bash или других языках.

## Когда нужны скрипты

Добавляйте скрипты, когда:

- Один и тот же код приходится писать заново каждый раз
- Задача требует детерминированного (точного) результата
- Есть сложная логика, которую нельзя описать текстом

## Структура навыка со скриптами

```
my-advanced-skill/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── scripts/
│   ├── process_data.py
│   └── generate_report.py
├── references/
│   └── api_docs.md
└── assets/
    └── template.html
```

## Пример: навык для анализа CSV

Создадим навык, который анализирует CSV-файлы.

### SKILL.md

```markdown
---
name: csv-analyzer
description: Анализ CSV-файлов — статистика, фильтрация, визуализация. Используйте, когда пользователь просит проанализировать, обобщить или визуализировать данные из CSV.
---

# CSV Analyzer

Анализ и визуализация данных из CSV-файлов.

## Использование

Для базовой статистики:
\`\`\`bash
python scripts/analyze.py data.csv
\`\`\`

Для визуализации:
\`\`\`bash
python scripts/analyze.py data.csv --chart bar --column revenue
\`\`\`

## Параметры

- `--chart` — тип графика (bar, line, pie)
- `--column` — столбец для анализа
- `--filter` — условие фильтрации
- `--output` — путь для сохранения результата
```

### scripts/analyze.py

```python
#!/usr/bin/env python3
import csv
import sys
import argparse
from collections import Counter

def analyze(filepath, column=None):
    with open(filepath) as f:
        reader = csv.DictReader(f)
        rows = list(reader)

    print(f"Строк: {len(rows)}")
    print(f"Столбцов: {len(rows[0]) if rows else 0}")
    print(f"Столбцы: {', '.join(rows[0].keys()) if rows else 'нет'}")

    if column and rows:
        values = [r[column] for r in rows if column in r]
        print(f"\nАнализ столбца '{column}':")
        print(f"  Уникальных значений: {len(set(values))}")
        print(f"  Примеры: {values[:5]}")

if __name__ == "__main__":
    parser = argparse.ArgumentParser()
    parser.add_argument("file", help="Путь к CSV")
    parser.add_argument("--column", help="Столбец для анализа")
    args = parser.parse_args()
    analyze(args.file, args.column)
```

## Ссылки на скрипты в SKILL.md

Всегда описывайте скрипты в SKILL.md:
- Что делает скрипт
- Какие параметры принимает
- Когда его запускать
- Примеры использования

## Работа с references/

Для больших справочных материалов используйте папку `references/`:

```markdown
## API

Подробное описание API — см. [references/api_docs.md](references/api_docs.md).
```

Codex загрузит файл только когда он понадобится.

## Итоги

- Скрипты добавляют навыкам точность и повторяемость
- Размещайте скрипты в папке `scripts/`
- Описывайте скрипты и их параметры в SKILL.md
- Используйте `references/` для больших справочных материалов
- Тестируйте каждый скрипт перед публикацией
