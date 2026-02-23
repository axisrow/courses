---
title: "Cascade AI Assistant"
weight: 6
bookToc: true
---

# Cascade AI Assistant

## What is Cascade?

Cascade is Windsurf's built-in AI assistant. Unlike simple autocomplete, Cascade can:

- Read and understand your entire project
- Make changes across multiple files
- Explain code and suggest improvements
- Run terminal commands on your behalf

## Opening Cascade

- Click the **Cascade icon** in the Activity Bar
- Press `Ctrl+Shift+L` (Windows/Linux) or `Cmd+Shift+L` (Mac)

## Modes

### Write Mode
Ask Cascade to write or edit code. Example prompts:

- "Create a REST API with Express.js"
- "Add error handling to the login function"
- "Write unit tests for the User class"

### Chat Mode
Ask questions without making changes:

- "Explain what this function does"
- "What is the best way to handle this error?"
- "Why is this test failing?"

## Using Cascade Effectively

### Be Specific
❌ "Fix the bug"
✅ "Fix the null pointer error in `processOrder()` on line 45"

### Provide Context
You can highlight code before opening Cascade. It will use the selection as context.

### Review Changes
Cascade shows a diff before applying changes. Always review before accepting.

## Example Workflow

1. Open Cascade
2. Type: "Add a login endpoint that validates email and password"
3. Review the suggested changes
4. Click **Accept** or **Reject** for each file
5. Test the result

## Limits

- Cascade works best with projects under 100 files
- Very large files may slow down responses
- Complex architectural changes may need multiple prompts

## Practice

Open a project and ask Cascade to add a new feature. Review the diff carefully before accepting.
