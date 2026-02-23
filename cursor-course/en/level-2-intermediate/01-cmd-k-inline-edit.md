---
title: "Cmd+K: Inline Editing with AI"
weight: 1
bookToc: true
---

# Cmd+K: Inline Editing with AI

## What Is Cmd+K?

`Cmd+K` (or `Ctrl+K` on Windows/Linux) opens an **inline prompt** right in your code. You describe what you want, and the AI edits the code in place.

This is more powerful than Tab completion because you give specific instructions.

## How to Use It

### Edit Existing Code
1. **Select** the code you want to change
2. Press `Cmd+K` / `Ctrl+K`
3. **Type your instruction** (e.g., "add error handling")
4. Press `Enter`
5. **Review** the changes — accept or reject

### Generate New Code
1. Place your cursor where you want new code
2. Press `Cmd+K` / `Ctrl+K` (without selecting anything)
3. Describe what you want (e.g., "create a login form component")
4. Press `Enter`

## Good Instructions

Be specific. Instead of vague requests, try:

| ❌ Vague | ✅ Specific |
|---------|-----------|
| "fix this" | "handle the case when the list is empty" |
| "make it better" | "add input validation and error messages" |
| "change the style" | "make the button blue with rounded corners" |

## Reviewing Changes

After the AI makes changes, you'll see a **diff view**:
- 🟢 Green lines = new code added
- 🔴 Red lines = old code removed

You can:
- **Accept** — Apply the changes
- **Reject** — Keep the original code
- **Edit the prompt** — Try a different instruction

## Real-World Examples

### Add Error Handling
Select a function → Cmd+K → "add try/catch and return meaningful error messages"

### Convert Code
Select code → Cmd+K → "convert this from JavaScript to TypeScript"

### Add Comments
Select code → Cmd+K → "add clear comments explaining each step"

## Summary

- `Cmd+K` / `Ctrl+K` = inline AI editing
- Select code first to edit, or place cursor to generate
- Be specific in your instructions
- Always review the diff before accepting
