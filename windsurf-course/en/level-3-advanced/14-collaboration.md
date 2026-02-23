---
title: "Team Collaboration"
weight: 14
bookToc: true
---

# Team Collaboration

## Working with a Team

Windsurf supports team workflows out of the box.

## Git Integration

### Basic Git Workflow
1. **Stage changes** — click `+` next to files in Source Control
2. **Commit** — write a message and click ✓
3. **Push/Pull** — sync with the remote

### AI Commit Messages
Windsurf can generate commit messages:
1. Stage your changes
2. Click the **AI sparkle icon** in the commit message box
3. Review and edit the generated message
4. Commit

## Code Reviews with AI

Before creating a pull request:
1. Ask Cascade: "Review my changes and find potential issues"
2. Fix any problems Cascade identifies
3. Ask: "Write a PR description for these changes"

## Shared Settings

Keep your team consistent with shared config:

```json
// .vscode/settings.json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.tabSize": 2
}
```

Commit this file to your repository.

## Pair Programming with AI

Use Windsurf as a "third team member":
- One person codes, the other reviews with Cascade
- Ask Cascade to explain unfamiliar code written by teammates
- Use Cascade to onboard new team members to the codebase

## Codeium Teams

Codeium offers a Teams plan with:
- Centralized billing
- Admin controls
- Usage analytics
- Custom AI model settings

Visit [codeium.com](https://codeium.com) for details.

## Practice

Set up a shared `.vscode/settings.json` in your project and use AI to generate commit messages for a week.
