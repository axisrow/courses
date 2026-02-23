---
title: "Writing Effective Prompts"
weight: 2
bookToc: true
---

# Writing Effective Prompts

## The Prompt File Structure

Every prompt in CodeMachine follows a specific structure:

```markdown
---
name: 'Step Name'
description: 'What this step does'
---

# Step Title

## STEP GOAL:
[Clear, one-sentence goal]

## MANDATORY EXECUTION RULES:
[Rules the agent must follow]

## Sequence of Instructions:
### 1. First task
### 2. Second task
### 3. Third task

## SUCCESS/FAILURE METRICS:
### SUCCESS: [What "done" looks like]
### FAILURE: [What counts as failure]
```

## Why Structure Matters

AI agents work best with clear, structured instructions. Without structure, agents:
- Skip steps
- Make assumptions
- Produce inconsistent results

With a good prompt, the agent follows your exact process every time.

## Tips for Writing Great Prompts

### Be Specific
❌ "Review the code"
✅ "Review the code in the `src/` folder. Check for security vulnerabilities, performance issues, and code style violations."

### Set Boundaries
Tell the agent what NOT to do:
```markdown
## CONTEXT BOUNDARIES:
- Do NOT modify any files
- Do NOT suggest changes to the database schema
- Focus ONLY on the frontend components
```

### Use Step-by-Step Instructions
Number your instructions. Agents follow numbered lists more reliably:
```markdown
### 1. Read the specification file at .codemachine/inputs/specifications.md
### 2. List all API endpoints mentioned
### 3. For each endpoint, document the expected input and output
### 4. Save the summary to .codemachine/outputs/api-summary.md
```

### Define Success Clearly
```markdown
## SUCCESS METRICS:
- All files in src/ have been reviewed
- A report has been generated at output/review.md
- No critical security issues remain unfixed
```

## Chained Prompts

For complex steps, you can split instructions into multiple prompt files:

```javascript
{
  id: 'planner',
  name: 'Planning Agent',
  promptPath: 'prompts/plan/main.md',
  chainedPromptsPath: [
    'prompts/plan/step-01-requirements.md',
    'prompts/plan/step-02-architecture.md',
    'prompts/plan/step-03-tasks.md',
  ],
}
```

The agent receives prompts one at a time, in order.

## Summary

- Follow the standard prompt structure
- Be specific and set clear boundaries
- Use numbered instructions
- Define success and failure metrics
- Use chained prompts for complex steps

> **Next lesson:** Running modes — interactive, autonomous, and continuous.
