---
title: "AI Refactoring"
weight: 7
bookToc: true
---

# AI Refactoring

## What is Refactoring?

Refactoring means improving your code without changing what it does. Windsurf makes this easy with AI.

## Quick Refactoring

1. Select the code you want to refactor
2. Right-click → **Windsurf: Refactor**
3. Or press `Ctrl+Shift+R`

## Common Refactoring Tasks

### Rename Variables
Select a variable and ask: "Rename to something more descriptive"

### Extract Function
Select a block of code and ask: "Extract this into a separate function"

### Simplify Logic
Select complex code and ask: "Simplify this logic"

### Convert Patterns
- "Convert this callback to async/await"
- "Convert this class component to a functional component"
- "Replace this for loop with map/filter"

## Using Cascade for Refactoring

Open Cascade and try:

```
Refactor the UserService class:
- Split into smaller methods
- Add proper error handling
- Use dependency injection
```

Cascade will show you a diff with all the changes.

## Before and After Example

**Before:**
```python
def process(d):
    r = []
    for i in d:
        if i['a'] > 10 and i['b'] == True:
            r.append(i['c'] * 2)
    return r
```

**After (AI refactored):**
```python
def process_active_items(items):
    return [
        item['value'] * 2
        for item in items
        if item['score'] > 10 and item['is_active']
    ]
```

## Tips

- Refactor small pieces at a time
- Always run tests after refactoring
- Use Git to commit before big refactors — easy to undo

## Practice

Find a function in your project with poor variable names. Use Windsurf to refactor it step by step.
