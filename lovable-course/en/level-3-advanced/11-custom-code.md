---
title: "Custom Code"
weight: 11
bookToc: true
---

# Custom Code

Go beyond prompts — edit code directly.

## Code View

Toggle the code view in the editor to see and edit generated files. Lovable creates clean React + TypeScript code.

## When to Edit Code

- Fine-tuning logic the AI didn't get right.
- Adding complex business rules.
- Integrating niche libraries.

## Editing Files

You can edit any file directly. Changes reflect in the preview instantly.

## Adding npm Packages

> Add the "date-fns" library for date formatting.

Lovable adds it to `package.json` and imports it where needed.

## Custom Hooks

> Create a custom React hook called useLocalStorage that persists state to localStorage.

## TypeScript Types

The generated code is fully typed. You can ask:

> Add proper TypeScript interfaces for the Product and Order types.

## File Structure

```
src/
  components/     ← UI components
  hooks/          ← Custom hooks
  lib/            ← Utilities
  pages/          ← Route pages
  integrations/   ← Supabase client
  types/          ← TypeScript types
```

## Combining Prompts and Code

The best workflow:
1. Use prompts for big changes.
2. Edit code for small tweaks.
3. The AI understands your manual edits and works around them.

## Summary

You have full access to the source code. Edit directly when needed, add packages, and create custom logic. Lovable respects your manual changes.
