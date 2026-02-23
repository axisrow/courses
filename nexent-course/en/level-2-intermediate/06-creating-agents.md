---
title: "Creating Agents with Prompts"
weight: 6
bookToc: true
---

# Creating Agents with Prompts

## The Core Idea

Nexent's most powerful feature is **smart agent prompt generation**. You describe what you want in plain language, and Nexent automatically:

- Generates the system prompt for the agent.
- Selects the right tools.
- Plans the best action path.

## Creating Your First Custom Agent

1. Navigate to the **Agents** section in the sidebar.
2. Click **Create New Agent**.
3. In the description field, type what you want — for example:

> "An assistant that helps HR teams screen resumes. It should read uploaded PDFs, compare candidates against job requirements, and rank them."

4. Click **Generate**. Nexent will create a complete agent configuration.
5. Review the generated prompt and tools. Adjust if needed.
6. Save and start chatting with your new agent.

## Tips for Writing Good Descriptions

- **State the role.** "You are a travel planner…"
- **Define the audience.** "…for families with young children."
- **List key tasks.** "You should suggest destinations, estimate budgets, and create day-by-day itineraries."
- **Mention constraints.** "Always recommend budget-friendly options under $2000."

## How Nexent Generates Prompts

Behind the scenes, Nexent uses a prompt generation pipeline:

1. Your description is analyzed by an AI model.
2. Relevant tools are identified from the MCP ecosystem.
3. A structured system prompt is generated with clear instructions.
4. The agent is configured and ready to use.

## Editing Agent Prompts

After generation, you can manually edit:

- **System prompt** — the core instructions.
- **Tool selection** — add or remove tools.
- **Knowledge base connections** — choose which knowledge bases the agent can access.

## Agent Versioning

Nexent keeps track of agent versions. Every time you save changes, a new version is created. You can:

- View version history.
- Roll back to a previous version.
- Compare versions side by side.

## Practice Exercise

Create an agent with this description:

> "A cooking assistant that suggests recipes based on ingredients I have at home. It should consider dietary restrictions and suggest substitutes for missing ingredients."

Test it by telling the agent what's in your fridge!
