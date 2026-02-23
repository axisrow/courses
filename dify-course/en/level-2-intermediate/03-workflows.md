---
title: "Workflows"
weight: 3
bookToc: true
---

# Workflows

## What is a Workflow?

A workflow is a visual chain of steps. Instead of one prompt, you connect multiple nodes to handle complex logic.

## When to Use Workflows

- Multi-step processing (e.g., classify → route → respond)
- Data transformation before or after LLM calls
- Conditional logic (if/else branching)
- Combining multiple tools and APIs

## Creating a Workflow

1. **Studio → Create App → Workflow**
2. You'll see a visual canvas with a **Start** node

## Node Types

| Node | Purpose |
|------|---------|
| **Start** | Entry point, defines input variables |
| **LLM** | Calls a language model |
| **Knowledge Retrieval** | Searches your knowledge base |
| **Code** | Runs Python or JavaScript |
| **IF/ELSE** | Conditional branching |
| **Template** | Formats text with Jinja2 |
| **HTTP Request** | Calls external APIs |
| **Variable Assigner** | Sets or transforms variables |
| **End** | Output node |

## Example: Smart Classifier

1. **Start** → user sends a question
2. **LLM** → classify: is it "sales", "support", or "other"?
3. **IF/ELSE** → branch based on classification
4. **LLM** (per branch) → generate specialized answer
5. **End** → return the answer

## Tips

- **Test each node** — click a node and use "Run" to test it alone
- **Use variables** — pass data between nodes via `{{node_name.output}}`
- **Keep it simple** — start small, add complexity gradually

## Next Step

Let's add external tools and plugins to your apps!
