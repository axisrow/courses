---
title: "Best Practices and Real-World Patterns"
weight: 5
bookToc: true
---

# Best Practices and Real-World Patterns

## Design Principles

### 1. Start Simple, Grow Complex

Begin with a 2-3 step workflow. Test it. Then add more steps, agents, and features.

```javascript
// Version 1: Simple
steps: [
  resolveStep('planner'),
  resolveStep('coder'),
]

// Version 2: With review
steps: [
  resolveStep('planner'),
  resolveStep('coder'),
  resolveStep('reviewer'),
]

// Version 3: With loops and sub-agents
steps: [
  resolveStep('planner'),
  resolveStep('coder'),
  resolveModule('quality-check', { loopSteps: 1 }),
  resolveStep('reviewer'),
],
subAgentIds: ['frontend-dev', 'backend-dev'],
```

### 2. One Agent, One Responsibility

Each agent should have a clear, focused task. Don't create "super agents" that do everything.

✅ Good:
- `code-reviewer` — reviews code quality
- `security-auditor` — checks for vulnerabilities
- `test-writer` — writes test cases

❌ Bad:
- `do-everything-agent` — reviews, audits, tests, and deploys

### 3. Write Prompts Like Recipes

Detailed, step-by-step instructions with clear success criteria:

```markdown
## STEP GOAL:
Review all JavaScript files in src/ for common security vulnerabilities.

## Sequence of Instructions:
### 1. List all .js and .ts files in src/
### 2. For each file, check for:
   - SQL injection vulnerabilities
   - XSS attack vectors
   - Hardcoded credentials
### 3. Create a report at output/security-report.md
### 4. Rate overall security: PASS / NEEDS ATTENTION / CRITICAL

## SUCCESS: Security report generated with ratings for every file
## FAILURE: Any file skipped or report missing
```

### 4. Use the Right Engine for the Job

| Task | Recommended Engine |
|------|-------------------|
| Code writing | Codex |
| Code review | Claude |
| Architecture | Claude |
| Documentation | Claude |
| Test generation | Codex |
| Refactoring | Codex |

### 5. Version Your Workflows

Keep workflows in version control (Git). Track changes to prompts, agents, and configurations.

## Common Workflow Templates

### Bug Fix Workflow
```javascript
steps: [
  resolveStep('reproducer'),      // Reproduce the bug
  resolveStep('analyzer'),        // Find the root cause
  resolveStep('fixer'),           // Implement the fix
  resolveModule('verifier', {     // Verify until passing
    loopSteps: 1,
    loopMaxIterations: 5,
  }),
]
```

### Feature Build Workflow
```javascript
steps: [
  resolveStep('researcher'),
  resolveStep('architect'),
  resolveStep('implementer'),
  resolveStep('reviewer'),
  resolveStep('test-writer'),
],
subAgentIds: ['frontend-dev', 'backend-dev'],
```

### Code Review Workflow
```javascript
steps: [
  resolveStep('style-checker'),
  resolveStep('security-auditor'),
  resolveStep('performance-analyzer'),
  resolveStep('report-generator'),
]
```

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Agent skips steps | Add "MANDATORY" rules and numbered instructions |
| Workflow loops forever | Set `loopMaxIterations` |
| Wrong engine used | Check agent config and step overrides |
| Context too large | Use context boundaries, split into smaller steps |
| Prompts not working | Check file paths in agent config |

## What's Next?

- Read the [official documentation](https://docs.codemachine.co)
- Join the [Discord community](https://discord.gg/vS3A5UDNSq)
- Explore the [Reddit community](https://www.reddit.com/r/CodeMachine/)
- Study the example workflows in `templates/workflows/`
- Build your own workflows and share them!

## Summary

- Start simple, add complexity gradually
- One agent, one job
- Write prompts like detailed recipes
- Match engines to task types
- Version control your workflows
- Use the community for inspiration and help

> **Congratulations!** You've completed the entire CodeMachine CLI course. You now have the knowledge to build powerful, automated AI workflows. Go build something amazing! 🚀
