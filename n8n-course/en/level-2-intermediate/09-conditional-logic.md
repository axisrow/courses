---
title: "Conditional Logic"
weight: 9
bookToc: true
---

# Conditional Logic

## Branching Workflows

Not all data should follow the same path. Conditional logic lets you route items based on rules.

## The IF Node

The simplest way to branch. It has two outputs: **True** and **False**.

### Conditions
- **String**: equals, contains, starts with, ends with, regex
- **Number**: equals, greater than, less than, between
- **Boolean**: is true, is false
- **Date**: before, after

### Example
```
Condition: {{ $json.amount }} > 100
True  → Send to manager for approval
False → Auto-approve
```

### Combining Conditions
- **AND** — All conditions must be true
- **OR** — At least one condition must be true

Example: amount > 100 AND department = "marketing"

## The Switch Node

Like IF but with multiple outputs. Route data to different paths based on a value.

### Example
```
Field: {{ $json.priority }}
Output 0: "low"    → Log to spreadsheet
Output 1: "medium" → Send email
Output 2: "high"   → Send Slack alert + email
Fallback:          → Ignore
```

## The Merge Node

After branching, you often need to bring data back together.

### Merge Modes
- **Append** — Combine all items from both inputs
- **Combine** — Match items from input 1 and input 2
  - By position (first with first, second with second)
  - By field (match on a shared key)
- **Choose Branch** — Only pass data from one input

## The Filter Node

Keep only items that match a condition. Unlike IF, it has one output — matching items pass through, others are dropped.

```
Filter: {{ $json.status }} equals "active"
→ Only active items continue
```

## Looping

### Loop Over Items
n8n processes items in batches by default. Each node receives all items and processes them.

### Split In Batches
For large datasets, process items in smaller groups:
1. Add **Split In Batches** node
2. Set batch size (e.g., 10)
3. Connect your processing nodes
4. Connect back to Split In Batches for the next batch

## Practical Example: Email Router

```
Email Trigger
  → IF (from VIP sender?)
    → True: Send Slack alert
    → False:
      → Switch (subject contains?)
        → "invoice"  → Save to accounting folder
        → "support"  → Create ticket
        → Fallback   → Archive
```

## Practice

Build a workflow that:
1. Uses Manual Trigger with sample data (5 items with name, age, country)
2. Filter: keep only age > 20
3. Switch: route by country to different Set nodes
4. Merge all results back together

## Summary

You now know how to create branching logic. Next, you will learn how to work with databases.
