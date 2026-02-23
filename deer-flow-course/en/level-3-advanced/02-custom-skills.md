---
title: "Creating Custom Skills"
weight: 2
bookToc: true
---

# Creating Custom Skills

## Introduction

DeerFlow's built-in skills cover many tasks, but the real power lies in creating **your own skills**. In this lesson you'll learn to create, test, and share custom Skills.

## Skill Structure

Each skill is a folder with a `SKILL.md` file:

```
skills/custom/
└── my-skill/
    └── SKILL.md
```

### SKILL.md Format

```markdown
---
name: data-analysis
description: "Data analysis with visualization"
license: MIT
allowed-tools:
  - bash
  - read_file
  - write_file
  - present_files
---

# Data Analysis

## Process

1. Read the uploaded data file
2. Determine data type and structure
3. Perform basic statistical analysis
4. Create visualizations (charts, graphs)
5. Write a report with conclusions
6. Save results to /mnt/user-data/outputs/

## Rules

- Always show first 5 rows of data
- Use pandas for processing
- Save charts in PNG format
- Write reports in the user's language
```

## Step-by-Step: Creating a Skill

### Step 1: Create the folder

```bash
mkdir -p skills/custom/email-writer
```

### Step 2: Create SKILL.md

```bash
cat > skills/custom/email-writer/SKILL.md << 'EOF'
---
name: email-writer
description: "Writing professional business emails"
license: MIT
allowed-tools:
  - write_file
  - present_files
---

# Business Email Writing

## Process

1. Ask the user: recipient, subject, tone (formal/informal)
2. Determine the email type (request, thank-you, complaint, proposal)
3. Write a draft following the template
4. Suggest subject line options
5. Save the final version

## Rules

- Maximum 200 words for a standard email
- Language — as requested by the user
- Suggest 2–3 subject line options
- Check grammar
EOF
```

### Step 3: Enable the skill

In `extensions_config.json`:

```json
{
  "skills": {
    "email-writer": {
      "enabled": true
    }
  }
}
```

Or via API:

```bash
curl -X PUT http://localhost:2026/api/skills/email-writer \
  -H "Content-Type: application/json" \
  -d '{"enabled": true}'
```

### Step 4: Test it

Restart DeerFlow and try:

```
Write a business email to a partner proposing a collaboration.
```

## Best Practices

1. **Be specific** — "Write a report with: title, summary (3 sentences), body, conclusions" beats "Write a good report"
2. **Limit tools** — only list `allowed-tools` that are actually needed
3. **Add examples** — include expected output samples in SKILL.md
4. **Use numbered steps** — helps the agent follow the logic
5. **Define rules** — explicitly state format, length, language, style constraints

## Sharing Skills

Skills can be packaged as `.skill` archives (ZIP):

```bash
cd skills/custom/email-writer
zip -r email-writer.skill .
```

Install via API:

```bash
curl -X POST http://localhost:2026/api/skills/install \
  -F "file=@email-writer.skill"
```

## Summary

- Custom skills are Markdown files in `skills/custom/`
- Format: YAML metadata + step-by-step instructions
- Skills can be enabled/disabled via configuration or API
- Distributed as .skill archives
- Best practices: specificity, limited tools, examples
