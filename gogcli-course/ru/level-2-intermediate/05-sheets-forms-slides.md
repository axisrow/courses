---
title: "Таблицы, Формы и Презентации"
weight: 10
bookToc: true
---

# Таблицы, Формы и Презентации

## Google Sheets (Таблицы)

### Чтение данных

```bash
gog sheets get SPREADSHEET_ID
gog sheets get SPREADSHEET_ID --range "Sheet1!A1:D10"
gog sheets get SPREADSHEET_ID --range "Sheet1!A:A" --format csv
```

### Запись данных

```bash
gog sheets set SPREADSHEET_ID --range "A1" --values "Привет,Мир"
gog sheets append SPREADSHEET_ID --range "Sheet1" --values "Новая,Строка,Данных"
```

### Создание таблицы

```bash
gog sheets create "Мой отчёт"
gog sheets create "Бюджет" --sheet "Январь" --sheet "Февраль"
```

## Google Forms (Формы)

### Просмотр форм

```bash
gog forms list
gog forms get FORM_ID
```

### Ответы на формы

```bash
gog forms responses FORM_ID
gog forms responses FORM_ID --format csv > ответы.csv
```

## Google Slides (Презентации)

### Работа с презентациями

```bash
gog slides list
gog slides get PRESENTATION_ID
gog slides export PRESENTATION_ID --format pdf -o презентация.pdf
```

## Практика

1. Создайте таблицу и добавьте в неё несколько строк
2. Прочитайте данные из таблицы в формате CSV
3. Экспортируйте презентацию в PDF
