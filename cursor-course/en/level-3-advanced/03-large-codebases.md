---
title: "Working with Large Codebases"
weight: 3
bookToc: true
---

# Working with Large Codebases

## The Challenge

Large projects have thousands of files. The AI can't read everything at once. You need strategies to help it focus.

## Indexing Your Codebase

Cursor **indexes** your project to enable fast search. This happens automatically when you open a folder. For large projects:
- Initial indexing may take a few minutes
- The index updates as you edit files
- Use `@codebase` to search the full index

## Strategies for Large Projects

### 1. Use Precise @mentions
Don't rely on the AI to find files. Point it directly:
```
@src/auth/middleware.ts @src/auth/types.ts Update the auth middleware to support API keys
```

### 2. Use .cursorignore
Create a `.cursorignore` file (like `.gitignore`) to exclude files the AI shouldn't read:
```
node_modules/
dist/
build/
*.min.js
coverage/
```

This makes indexing faster and AI responses more focused.

### 3. Break Tasks Into Pieces
Instead of "refactor the entire authentication system," ask:
1. "List all files related to authentication"
2. "Refactor the login function in auth/login.ts"
3. "Update the tests in auth/__tests__/"

### 4. Use Documentation as Context
If your project has docs, reference them:
```
@docs/architecture.md Help me add a new service following this architecture
```

## Performance Tips

- **Close unused tabs** — Open files add to the AI's context
- **Use specific searches** — `@codebase findUserById` is better than `@codebase user`
- **Keep .cursorignore updated** — Exclude generated files and dependencies

## Summary

- Use `@mentions` to guide the AI to specific files
- Create `.cursorignore` to exclude irrelevant files
- Break large tasks into smaller, focused requests
- Index your codebase for fast search with `@codebase`
