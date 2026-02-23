---
title: "Custom Functions and Code Node"
weight: 11
bookToc: true
---

# Custom Functions and Code Node

## When to Use Code

Use the Code node when built-in nodes are not enough:
- Complex data transformations
- Custom business logic
- Mathematical calculations
- Text parsing and formatting

## The Code Node

Supports **JavaScript** and **Python**.

### Run Once for All Items

Process all items together:

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

### Run Once for Each Item

Process items one at a time:

```javascript
const name = $json.firstName + ' ' + $json.lastName;
const age = Math.floor((Date.now() - new Date($json.birthDate)) / 31557600000);

return {
  json: {
    fullName: name,
    age: age,
    isAdult: age >= 18
  }
};
```

## Useful JavaScript Patterns

### Grouping Data
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

### Deduplication
```javascript
const seen = new Set();
return $input.all().filter(item => {
  const key = item.json.email;
  if (seen.has(key)) return false;
  seen.add(key);
  return true;
});
```

### Date Formatting
```javascript
const date = new Date($json.timestamp);
return {
  json: {
    ...$json,
    formatted: date.toISOString().split('T')[0],
    dayOfWeek: ['Sun','Mon','Tue','Wed','Thu','Fri','Sat'][date.getDay()]
  }
};
```

## Accessing Other Nodes

```javascript
// Get data from a specific node
const userData = $node["HTTP Request"].json;

// Get all items from a node
const allItems = $("HTTP Request").all();

// Get the first item
const firstItem = $("HTTP Request").first();
```

## External Libraries

n8n Code node includes built-in libraries:
- `lodash` — Utility functions
- `moment` — Date handling
- `crypto` — Hashing and encryption

```javascript
const _ = require('lodash');
const grouped = _.groupBy($input.all().map(i => i.json), 'status');
```

## Error Handling in Code

```javascript
try {
  const data = JSON.parse($json.rawData);
  return { json: { parsed: data, success: true } };
} catch (err) {
  return { json: { error: err.message, success: false } };
}
```

## Practice

1. Fetch users from an API
2. Use a Code node to: calculate age from birthdate, create a full name, classify users into age groups
3. Output clean, formatted data

## Summary

The Code node gives you unlimited flexibility. Next, you will learn about webhooks and advanced integrations.
