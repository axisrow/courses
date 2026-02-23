---
title: "Creating Plugins"
weight: 3
bookToc: true
---

# Creating Plugins

## Introduction

Pi supports extension through Extensions, Skills, Prompt Templates, and Themes. Package them as Pi Packages and share via npm.

## Extensions

Extensions add new tools to the agent. Create a file in `.pi/extensions/`:

```typescript
// .pi/extensions/time.ts
import { Type } from '@mariozechner/pi-ai';

export default {
  name: 'current_time',
  description: 'Returns current time',
  parameters: Type.Object({}),
  execute: async () => {
    return new Date().toISOString();
  },
};
```

## Skills

Skills are text files with instructions:

```bash
mkdir -p .pi/skills
cat > .pi/skills/git.md << 'EOF'
When working with Git:
- Always create feature branches
- Write meaningful commit messages
- Use conventional commits
EOF
```

## Prompt Templates

Custom system prompts for different tasks:

```bash
cat > .pi/prompts/reviewer.md << 'EOF'
You are a code reviewer. Analyze code for:
- Security
- Performance
- Readability
EOF
```

## Pi Packages

Package extensions as npm packages:

```json
{
  "name": "my-pi-package",
  "pi": {
    "extensions": ["./extensions/"],
    "skills": ["./skills/"],
    "prompts": ["./prompts/"]
  }
}
```

## Summary

- Extensions add tools
- Skills provide instructions
- Prompt Templates define behavior
- Pi Packages let you share everything
