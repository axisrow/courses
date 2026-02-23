---
title: "Multi-file Editing"
weight: 8
bookToc: true
---

# Multi-file Editing

## Why Multi-file?

Real projects have many files. When you add a feature, you often need to change several files at once. Windsurf understands this.

## How Cascade Handles Multiple Files

When you ask Cascade to make a change, it can:

1. **Read** related files to understand the context
2. **Edit** multiple files in one action
3. **Create** new files as needed
4. **Show diffs** for each file separately

## Example: Adding a New API Endpoint

Prompt to Cascade:
```
Add a GET /api/users/:id endpoint that returns user data from the database
```

Cascade might edit:
- `routes/users.js` — add the route
- `controllers/userController.js` — add the handler
- `models/user.js` — verify the model
- `tests/users.test.js` — add a test

## Reviewing Multi-file Changes

1. Cascade shows a list of affected files
2. Click each file to see the diff
3. Accept or reject changes per file
4. You can accept all at once if you trust the changes

## Tips for Multi-file Prompts

- **Mention the architecture**: "Using MVC pattern, add..."
- **Reference specific files**: "Update `config.js` and `server.js` to..."
- **Describe the full feature**: The more context, the better

## Limitations

- Cascade reads open files and nearby files
- Very large projects may need you to point Cascade to specific folders
- Binary files (images, etc.) are skipped

## Practice

Ask Cascade to add a complete feature (e.g., user registration) and observe how it modifies multiple files.
