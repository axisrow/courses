---
title: "Context Engineering"
weight: 2
bookToc: true
---

# Context Engineering

## Why Context Matters

AI agents perform best when they receive exactly the right information — not too much, not too little. Context engineering is the art of controlling what each agent sees.

## Placeholders

Placeholders inject dynamic content into prompts. Define them in `config/placeholders.js`:

```javascript
export default {
  userDir: {
    project_specs: 'inputs/specifications.md',
    api_docs: 'inputs/api-documentation.md',
  },
  packageDir: {
    step_completion: 'shared/step-completion.md',
    coding_standards: 'shared/coding-standards.md',
  },
};
```

Use placeholders in prompts with curly braces:

```markdown
# Implementation Step

## Project Requirements:
{project_specs}

## Coding Standards:
{coding_standards}

## When you finish:
{step_completion}
```

- **userDir** — files from your project's `.codemachine` folder
- **packageDir** — files from CodeMachine's built-in templates

## Context Boundaries

Tell agents what they should and shouldn't access:

```markdown
## CONTEXT BOUNDARIES:
- Read ONLY files in the src/components/ directory
- Do NOT modify package.json
- Do NOT access environment variables
- Use ONLY the APIs documented in {api_docs}
```

## Passing Context Between Steps

Each step's output becomes available as context for the next step. CodeMachine handles this automatically. However, you can be explicit:

```markdown
## Sequence of Instructions:
### 1. Read the output from the previous step
### 2. Build upon the architecture defined there
### 3. Save your implementation plan to .codemachine/outputs/plan.md
```

## The Specification File

The specification file (`.codemachine/inputs/specifications.md`) is a central document describing your project. You can pass it to CodeMachine:

```bash
codemachine --spec path/to/my-spec.md
```

Many prompts reference this file using the `{project_specs}` placeholder.

## Best Practices

1. **Less is more** — Give agents only the information they need
2. **Structured input** — Use markdown with headers, lists, tables
3. **Explicit boundaries** — Always state what's off-limits
4. **Shared templates** — Reuse common instructions via placeholders

## Summary

- Placeholders inject dynamic content into prompts
- Context boundaries keep agents focused
- Context flows automatically between steps
- The specification file is your project's central document
- Give agents exactly what they need, nothing more

> **Next lesson:** Orchestration patterns — from interactive to fully autonomous.
