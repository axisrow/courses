---
title: "Data Transformation"
weight: 7
bookToc: true
---

# Data Transformation

## Why Transform Data?

Data from one service rarely matches the format another service expects. You need to rename fields, filter items, split or merge data, and calculate new values.

## Expressions

Expressions are the core of data transformation in n8n. They use the `{{ }}` syntax.

### Basic Expressions
- `{{ $json.name }}` — Access a field
- `{{ $json.price * 1.2 }}` — Calculate
- `{{ $json.name.toUpperCase() }}` — Transform text
- `{{ $json.date.split('T')[0] }}` — Extract part of a string

### Special Variables
- `$json` — Current item's data
- `$input` — All input data
- `$node["NodeName"].json` — Data from a specific node
- `$now` — Current date/time
- `$runIndex` — Current execution number

## Key Transformation Nodes

### Set Node
Rename, add, or remove fields:
- **Add Value** — Create new fields
- **Keep Only Set** — Remove all fields except the ones you define

### Code Node
Write JavaScript or Python for complex transformations:

```javascript
// Process each item
return items.map(item => {
  item.json.fullName = item.json.firstName + ' ' + item.json.lastName;
  item.json.isAdult = item.json.age >= 18;
  return item;
});
```

### Split Out Node
Turn an array field into separate items:
- Input: 1 item with `tags: ["a", "b", "c"]`
- Output: 3 items, one per tag

### Aggregate Node
Combine multiple items into one:
- Input: 5 separate items
- Output: 1 item with all values in an array

### Sort Node
Reorder items by a field value (ascending or descending).

### Limit Node
Keep only the first N items.

### Remove Duplicates Node
Eliminate duplicate items based on a field.

## Common Patterns

### Rename Fields
```
Set node → Add value "email" = {{ $json.contact_email }}
         → Keep Only Set: ON
```

### Filter Items
```
IF node → Condition: {{ $json.status }} equals "active"
       → True branch continues, False branch is ignored
```

### Merge Two Data Sources
```
Merge node → Mode: Combine
           → Join based on a matching field
```

## Practice

1. Fetch a list of users from `https://jsonplaceholder.typicode.com/users`
2. Extract only `name`, `email`, and `city` (from `address.city`)
3. Sort by name
4. Keep only the first 5

## Summary

You now know how to transform data between nodes. Next, you will learn how to handle errors in your workflows.
