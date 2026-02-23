---
title: "Gmail: подробный разбор"
weight: 6
bookToc: true
---

# Gmail: подробный разбор

Полное управление электронной почтой из командной строки.

## Поиск писем

gogcli использует тот же синтаксис поиска, что и веб-интерфейс Gmail:

```bash
# Письма за 7 дней
gog gmail search 'newer_than:7d' --max 20

# От конкретного человека
gog gmail search 'from:alice@example.com' --max 10

# С вложениями
gog gmail search 'has:attachment newer_than:30d'

# Только непрочитанные
gog gmail search 'is:unread' --max 20

# Комбинация критериев
gog gmail search 'from:boss@company.com subject:urgent newer_than:1d'
```

### Поиск по отдельным сообщениям

```bash
gog gmail messages search 'newer_than:7d' --max 10

# С текстом сообщения
gog gmail messages search 'newer_than:7d' --max 5 --include-body
```

## Чтение писем

```bash
gog gmail thread get THREAD_ID
gog gmail get MESSAGE_ID
gog gmail thread get THREAD_ID --download --out-dir ./вложения
```

## Отправка писем

```bash
# Простое письмо
gog gmail send --to recipient@example.com --subject "Привет" --body "Здравствуйте!"

# HTML-письмо
gog gmail send --to recipient@example.com --subject "Отчёт" \
  --body "Текстовая версия" \
  --body-html "<h1>Отчёт</h1><p>Смотрите вложение.</p>"

# Тело из файла
gog gmail send --to recipient@example.com --subject "Заметки" --body-file ./notes.txt

# Ответ с цитированием оригинала
gog gmail send --reply-to-message-id MSG_ID --quote \
  --to recipient@example.com --subject "Re: Привет" --body "Спасибо!"
```

## Управление ярлыками

```bash
gog gmail labels list
gog gmail labels create "Проекты/Активные"
gog gmail thread modify THREAD_ID --add STARRED --remove INBOX
gog gmail labels delete "Старый ярлык"
```

## Черновики

```bash
gog gmail drafts list
gog gmail drafts create --to bob@example.com --subject "Черновик" --body "В работе..."
gog gmail drafts send DRAFT_ID
```

## Фильтры

```bash
gog gmail filters list
gog gmail filters create --from 'noreply@example.com' --add-label 'Уведомления'
gog gmail filters delete FILTER_ID
```

## Пакетные операции

```bash
gog gmail batch modify MSG_ID1 MSG_ID2 --add STARRED
gog gmail batch delete MSG_ID1 MSG_ID2
```

## Автоответчик

```bash
gog gmail vacation get
gog gmail vacation enable --subject "Не в офисе" --message "Вернусь в понедельник."
gog gmail vacation disable
```

## Далее

В следующем уроке вы освоите управление Календарём.
