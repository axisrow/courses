---
title: "Tab Completion — Your AI Copilot"
weight: 5
bookToc: true
---

# Tab Completion — Your AI Copilot

## What Is Tab Completion?

As you type code, Cursor predicts what you want to write next. Suggestions appear as **gray text** after your cursor. Press `Tab` to accept.

This is the simplest and most common way to use AI in Cursor.

## How It Works

1. **You type** a few characters or a line of code
2. **Cursor suggests** the next line, block, or even entire function
3. **Press Tab** to accept, or keep typing to ignore

The AI looks at:
- What you've typed so far
- Other files in your project
- The programming language you're using
- Common coding patterns

## Examples

### Example 1: Writing a Function
You type:
```python
def calculate_total(items):
```
Cursor suggests:
```python
    total = 0
    for item in items:
        total += item.price
    return total
```
Press `Tab` to accept the entire suggestion.

### Example 2: Writing Comments First
You type a comment:
```javascript
// function that checks if an email is valid
```
Cursor suggests the complete function below your comment.

### Example 3: Repetitive Patterns
If you've written:
```python
user.first_name = data["first_name"]
user.last_name = data["last_name"]
```
Cursor predicts the next field automatically.

## Tips for Better Suggestions

1. **Write clear comments** — The AI reads your comments to understand intent
2. **Use descriptive names** — `calculateTotalPrice` gets better suggestions than `calc`
3. **Keep related files open** — Cursor uses open files as context
4. **Be patient** — Sometimes suggestions appear after a brief pause

## Accepting Partial Suggestions

- **Tab** — Accept the full suggestion
- **Ctrl+→** / **Cmd+→** — Accept word by word
- **Escape** — Dismiss the suggestion

## When Tab Completion Isn't Enough

Tab completion is great for line-by-line coding. But when you need bigger changes — rewriting a block, refactoring, or building a new feature — you'll want **Cmd+K** (inline edit) or **Chat** mode. We'll cover those in Level 2!

## Summary

- AI suggestions appear as gray text
- Press `Tab` to accept
- Write clear comments and names for better results
- This is just the beginning — more powerful tools await!
