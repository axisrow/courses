---
title: "Google Диск и файлы"
weight: 8
bookToc: true
---

# Google Диск и файлы

Загрузка, скачивание, организация и обмен файлами из терминала.

## Просмотр файлов

```bash
gog drive ls --max 20
gog drive ls --parent FOLDER_ID --max 20
gog drive search "квартальный отчёт" --max 10
```

## Скачивание

```bash
gog drive download FILE_ID --out ./файл.pdf
gog drive download DOC_ID --format pdf --out ./документ.pdf
gog drive download DOC_ID --format docx --out ./документ.docx
```

## Загрузка

```bash
gog drive upload ./отчёт.pdf --parent FOLDER_ID
gog drive upload ./отчёт.docx --convert
gog drive upload ./отчёт-v2.pdf --replace FILE_ID
```

## Организация

```bash
gog drive mkdir "Отчёты за Q1"
gog drive rename FILE_ID "Новое имя"
gog drive move FILE_ID --parent DEST_FOLDER_ID
gog drive delete FILE_ID
```

## Общий доступ

```bash
gog drive permissions FILE_ID
gog drive share FILE_ID --to user --email colleague@example.com --role reader
gog drive share FILE_ID --to user --email colleague@example.com --role writer
gog drive unshare FILE_ID --permission-id PERM_ID
```

## Работа с Документами

```bash
gog docs info DOC_ID
gog docs cat DOC_ID
gog docs create "Заметки со встречи"
gog docs create "Отчёт" --file ./report.md
gog docs export DOC_ID --format pdf --out ./doc.pdf
```

## Работа с Таблицами

```bash
gog sheets metadata SPREADSHEET_ID
gog sheets get SPREADSHEET_ID 'Sheet1!A1:D10'
gog sheets update SPREADSHEET_ID 'A1' 'Имя|Возраст,Алиса|30,Борис|25'
gog sheets append SPREADSHEET_ID 'Sheet1!A:C' 'Чарли|28|Лондон'
gog sheets create "Бюджет 2025" --sheets "Доходы,Расходы"
```

## Общие диски

```bash
gog drive drives --max 100
```

## Далее

В следующем уроке — Контакты и Задачи.
