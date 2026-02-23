---
title: "Using Context: @files, @docs, @web"
weight: 3
bookToc: true
---

# Using Context: @files, @docs, @web

## Why Context Matters

The AI works best when it knows what you're working with. **Context mentions** (using the `@` symbol) let you point the AI to specific information.

## Types of Mentions

### @files — Reference Your Code
Type `@filename` in chat or Cmd+K to include a specific file:

```
@utils.py How can I improve the error handling in this file?
```

The AI reads the entire file and gives specific advice.

### @folder — Include Entire Folders
```
@src/components Help me create a new component that matches the existing style
```

### @docs — Reference Documentation
```
@docs Search the Next.js documentation for how to use server components
```

Cursor can read official documentation for popular frameworks.

### @web — Search the Internet
```
@web What's the latest way to handle authentication in React 2025?
```

The AI searches the web and uses fresh information in its answer.

### @codebase — Search Your Whole Project
```
@codebase Where is the database connection configured?
```

Cursor searches across all files in your project.

## Combining Mentions

You can use multiple mentions in one prompt:
```
@api/routes.py @models/user.py Add a new endpoint to delete users, following the existing pattern
```

## When to Use What

| Situation | Use |
|-----------|-----|
| Edit a specific file | `@filename` |
| Follow project patterns | `@folder` |
| Use framework docs | `@docs` |
| Need latest info | `@web` |
| Find something in project | `@codebase` |

## Summary

- Use `@` mentions to give the AI precise context
- `@files` for specific files, `@web` for internet search
- `@codebase` searches your entire project
- Better context = better AI responses
