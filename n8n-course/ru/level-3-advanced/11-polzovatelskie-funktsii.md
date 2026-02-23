---
title: "Пользовательские функции и Code Node"
weight: 11
bookToc: true
---

# Пользовательские функции и Code Node

## Когда нужен код

Code Node — когда стандартных нодов не хватает:
- Сложные преобразования данных
- Пользовательская бизнес-логика
- Математические расчёты
- Парсинг текста

## Code Node

Поддерживает **JavaScript** и **Python**.

### Обработка всех элементов

```javascript
const results = [];
for (const item of $input.all()) {
  results.push({
    json: {
      name: item.json.name.trim(),
      email: item.json.email.toLowerCase(),
      score: item.json.points / item.json.maxPoints * 100
    }
  });
}
return results;
```

### Обработка по одному

```javascript
const name = $json.firstName + ' ' + $json.lastName;
const age = Math.floor((Date.now() - new Date($json.birthDate)) / 31557600000);
return {
  json: { fullName: name, age, isAdult: age >= 18 }
};
```

## Полезные паттерны

### Группировка
```javascript
const grouped = {};
for (const item of $input.all()) {
  const key = item.json.category;
  if (!grouped[key]) grouped[key] = [];
  grouped[key].push(item.json);
}
return Object.entries(grouped).map(([category, items]) => ({
  json: { category, items, count: items.length }
}));
```

### Дедупликация
```javascript
const seen = new Set();
return $input.all().filter(item => {
  const key = item.json.email;
  if (seen.has(key)) return false;
  seen.add(key);
  return true;
});
```

## Доступ к другим нодам

```javascript
const userData = $node["HTTP Request"].json;
const allItems = $("HTTP Request").all();
const firstItem = $("HTTP Request").first();
```

## Встроенные библиотеки

- `lodash` — утилиты
- `moment` — даты
- `crypto` — хеширование

## Обработка ошибок

```javascript
try {
  const data = JSON.parse($json.rawData);
  return { json: { parsed: data, success: true } };
} catch (err) {
  return { json: { error: err.message, success: false } };
}
```

## Практика

1. Получите пользователей из API
2. Code Node: рассчитайте возраст, создайте полное имя, классифицируйте по возрасту
3. Выведите чистые данные

## Итог

Code Node даёт неограниченную гибкость. Далее — вебхуки и интеграции.
