---
title: "Custom Rules & .cursorrules"
weight: 2
bookToc: true
---

# Custom Rules & .cursorrules

## What Are Custom Rules?

You can tell Cursor **how** to write code for your project. Custom rules ensure the AI follows your coding style, conventions, and preferences.

## The .cursorrules File

Create a file called `.cursorrules` in your project root. This file contains instructions the AI will follow for every interaction.

### Example .cursorrules

```
You are helping with a React TypeScript project.

Rules:
- Use functional components with hooks (no class components)
- Use TypeScript strict mode
- Write tests for every new function using Vitest
- Use Tailwind CSS for styling
- Follow the existing folder structure in src/
- Add JSDoc comments to all exported functions
- Handle errors with try/catch, never silently fail
- Use English for all code comments
```

## Global Rules vs. Project Rules

- **Project rules** (`.cursorrules` file) — Apply to one project only
- **Global rules** (Settings → Cursor → Rules) — Apply to all your projects

## What to Include in Rules

- **Language & framework** preferences
- **Coding style** (naming conventions, formatting)
- **Testing** requirements
- **Documentation** standards
- **Error handling** patterns
- **Things to avoid** (deprecated APIs, certain libraries)

## Tips

- Keep rules **concise** — The AI reads them every time
- Be **specific** — "Use camelCase for variables" is better than "use good naming"
- **Update regularly** — As your project evolves, update the rules
- **Share with your team** — Commit `.cursorrules` to Git so everyone uses the same rules

## Summary

- `.cursorrules` defines how the AI writes code for your project
- Place it in your project root
- Include style, framework, testing, and documentation rules
- Keep it concise and specific
