---
title: "Чтение и использование результатов"
weight: 5
bookToc: true
---

# Чтение и использование результатов

## Понимание выходных данных

PageIndex создаёт JSON-файл с полной древовидной структурой. Разберём, как его читать и использовать.

## Структура вывода

```json
{
  "doc_name": "2023-annual-report",
  "structure": [
    {
      "title": "Письмо акционерам",
      "node_id": "0001",
      "start_index": 1,
      "end_index": 3,
      "summary": "Генеральный директор обсуждает достижения..."
    },
    {
      "title": "Финансовый обзор",
      "node_id": "0002",
      "start_index": 4,
      "end_index": 50,
      "summary": "Финансовые результаты за 2023 год",
      "nodes": [
        {
          "title": "Анализ выручки",
          "node_id": "0003",
          "start_index": 4,
          "end_index": 15
        }
      ]
    }
  ]
}
```

## Ключевые поля

### Индексы страниц
- **start_index**: Первая страница раздела (начиная с 1)
- **end_index**: Последняя страница раздела

### Идентификаторы узлов
Каждый раздел получает уникальный **node_id**. Полезно для ссылок на конкретные разделы в приложении.

### Резюме
Поле **summary** содержит краткое описание раздела. Резюме критически важны для поиска по дереву.

### Вложенные узлы
Массив **nodes** содержит дочерние разделы — это создаёт иерархию.

## Практические советы

### Совет 1: Обход дерева программно

```python
import json

with open("results/document_structure.json") as f:
    data = json.load(f)

def print_tree(nodes, indent=0):
    for node in nodes:
        pages = f"(стр. {node['start_index']}-{node['end_index']})"
        print("  " * indent + f"- {node['title']} {pages}")
        if "nodes" in node:
            print_tree(node["nodes"], indent + 1)

print_tree(data["structure"])
```

### Совет 2: Поиск раздела по теме

```python
def find_sections(nodes, keyword):
    results = []
    for node in nodes:
        if keyword.lower() in node.get("summary", "").lower():
            results.append(node)
        if "nodes" in node:
            results.extend(find_sections(node["nodes"], keyword))
    return results
```

### Совет 3: Извлечение страниц

Зная `start_index` и `end_index`, можно извлечь нужные страницы из PDF с помощью любой библиотеки для работы с PDF.

## Итоги

Выходные данные PageIndex — это структурированное JSON-дерево с названиями, диапазонами страниц, идентификаторами и резюме. Понимание этого формата позволяет строить мощные приложения поверх PageIndex.
