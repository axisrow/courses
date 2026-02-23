---
title: "Multi-file Editing"
weight: 5
bookToc: true
---

# Multi-file Editing

## Beyond Single Files

Real projects have dozens or hundreds of files. Cursor's AI can understand and edit **multiple files at once**.

## How It Works

When you ask the AI to make a change in Chat, it can:
1. **Identify** which files need to change
2. **Propose edits** across multiple files
3. **Show you a diff** for each file
4. Let you **accept or reject** each change individually

## Example: Adding a New Feature

Imagine you ask:
```
Add a "forgot password" feature with an email form, API endpoint, and email sending logic
```

Cursor might propose changes to:
- `pages/forgot-password.tsx` — New page with the form
- `api/auth/reset.ts` — New API endpoint
- `lib/email.ts` — Email sending function
- `lib/routes.ts` — Updated route configuration

## Reviewing Multi-file Changes

After the AI generates changes:
1. You see a list of all affected files
2. Click each file to see the diff
3. **Accept** or **Reject** each file individually
4. You can also edit the changes before accepting

## Tips

- **Use @mentions** to point the AI to relevant files
- **Be explicit** about which files you want changed
- **Review carefully** — The AI may change files you didn't expect
- **Use Git** — Always commit before large multi-file changes so you can revert

## Composer Mode

For complex multi-file tasks, use **Composer** (Ctrl+I / Cmd+I):
- Designed for multi-file edits
- Shows all changes in one view
- Better for large refactoring tasks

## Summary

- Cursor can edit multiple files in a single request
- Review each file's changes individually
- Use Composer for complex multi-file operations
- Always use Git as a safety net
