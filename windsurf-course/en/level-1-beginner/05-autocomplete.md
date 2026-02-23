---
title: "Basic AI Autocomplete"
weight: 5
bookToc: true
---

# Basic AI Autocomplete

## How It Works

Windsurf uses AI to predict what you want to type next. As you write code, suggestions appear as gray text. This is called **ghost text**.

## Accepting Suggestions

- **Tab** — accept the full suggestion
- **Ctrl+→** — accept word by word
- **Escape** — dismiss the suggestion

## Types of Completions

### 1. Single Line
When you start typing a line, Windsurf completes it:

```javascript
const greeting = "Hello, " // AI suggests: + name + "!"
```

### 2. Multi-line
After a function signature or comment, Windsurf can write the full body:

```python
def fibonacci(n):
    # AI writes the entire function body
```

### 3. Comment-driven
Write a comment describing what you need. The AI turns it into code:

```javascript
// fetch user data from API and return the name
```

## Tips for Better Suggestions

1. **Write clear variable names** — `userEmail` gets better results than `x`
2. **Add comments** — they guide the AI
3. **Provide context** — import statements help the AI understand your project
4. **Be specific** — "sort array of objects by date descending" works better than "sort this"

## Languages Supported

Windsurf supports 70+ languages, including:
Python, JavaScript, TypeScript, Java, C++, Go, Rust, PHP, Ruby, Swift, and many more.

## Settings

You can adjust autocomplete behavior in Settings:
- Enable/disable autocomplete
- Change suggestion delay
- Filter by file type

## Practice

1. Open a new file in any language
2. Write 3 comments describing different functions
3. Let Windsurf generate each one
4. Review and edit the results
