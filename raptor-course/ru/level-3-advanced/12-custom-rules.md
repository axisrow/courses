---
title: "Создание собственных правил Semgrep и CodeQL"
weight: 2
bookToc: true
---

## Создание собственных правил Semgrep и CodeQL

### Зачем нужны свои правила?

Встроенные правила RAPTOR покрывают типичные уязвимости, но ваше приложение может иметь уникальные паттерны.

### Пользовательские правила Semgrep

Правила Semgrep пишутся на YAML:

```yaml
rules:
  - id: my-custom-rule
    pattern: |
      dangerous_function($INPUT)
    message: "Ненадёжный ввод передан в dangerous_function"
    severity: ERROR
    languages: [python]
    metadata:
      category: security
      cwe: CWE-78
```

#### Добавление правил в RAPTOR

Поместите правила в:
```
engine/semgrep/rules/your-category/your-rule.yaml
```

### Пользовательские запросы CodeQL

Запросы CodeQL используют SQL-подобный язык QL:

```ql
import python
import semmle.python.dataflow.new.DataFlow

from DataFlow::Node source, DataFlow::Node sink
where
  source.asExpr() instanceof UserInput and
  sink.asExpr() = dangerousCall.getAnArgument()
select sink, "Ненадёжные данные попадают в опасную функцию"
```

### Инструмент SARIF Merge

RAPTOR включает инструмент слияния SARIF (`engine/semgrep/tools/sarif_merge.py`) для объединения результатов нескольких сканеров.

### Тестирование правил

1. Напишите тестовый файл с уязвимым паттерном
2. Поместите его в `test/data/`
3. Запустите правило
4. Убедитесь, что оно обнаруживает проблему без ложных срабатываний

### Главный вывод

Собственные правила позволяют адаптировать RAPTOR под вашу кодовую базу. Начните с правил Semgrep (проще писать), затем переходите к CodeQL для анализа потоков данных.
