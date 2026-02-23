---
title: "Debugging with AI"
weight: 9
bookToc: true
---

# Debugging with AI

## AI-Assisted Debugging

Finding bugs is one of the hardest parts of programming. Windsurf helps in several ways.

## Method 1: Ask Cascade

Copy an error message and paste it into Cascade:

```
I'm getting this error: "TypeError: Cannot read property 'map' of undefined"
in UserList.jsx line 15
```

Cascade will:
1. Look at the file
2. Explain what causes the error
3. Suggest a fix

## Method 2: Inline Error Explanation

When you see a red underline in your code:
1. Hover over it to see the error
2. Click **Quick Fix** (or `Ctrl+.`)
3. Windsurf may offer AI-powered fixes

## Method 3: Debug with Terminal

Ask Cascade:
```
Run the tests and explain why they are failing
```

Cascade can execute commands and analyze the output.

## Common Debugging Scenarios

### Null/Undefined Errors
Ask: "Why could `user.name` be undefined here?"

### Logic Bugs
Highlight the function and ask: "This function returns wrong results for negative numbers. Can you find the bug?"

### Performance Issues
Ask: "Why is this function slow? How can I optimize it?"

### API Errors
Share the error response: "I'm getting a 403 from this API call. Here's my code..."

## Debugging Tips

1. **Share the full error** — include stack traces
2. **Describe expected vs actual behavior**
3. **Mention what you already tried**
4. **Use breakpoints** — Windsurf supports standard VS Code debugging

## Practice

Find a bug in your code (or introduce one on purpose). Ask Cascade to help you find and fix it.
