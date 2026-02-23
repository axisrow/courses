---
title: "Contributing to openai/skills"
weight: 5
bookToc: true
---

# Contributing to openai/skills

## Introduction

If you've built a useful skill, you can propose it to the official [openai/skills](https://github.com/openai/skills) repository.

## Community Values

- **Be kind and inclusive** — respect other contributors
- **Assume good intent** — written communication is hard
- **Teach and learn** — if something is confusing, open an issue or PR

## Contribution Process

### Step 1: Fork the Repository

Go to [github.com/openai/skills](https://github.com/openai/skills) and click "Fork".

### Step 2: Clone Your Fork

```bash
git clone https://github.com/your-username/skills.git
cd skills
```

### Step 3: Create a Branch

```bash
git checkout -b add-my-skill
```

### Step 4: Add Your Skill

Place your skill in the appropriate folder:

- `skills/.experimental/` — for new, experimental skills
- `skills/.curated/` — by invitation or after review only

```bash
cp -r ~/my-skill skills/.experimental/my-skill
```

### Step 5: Validate

```bash
python skills/.system/skill-creator/scripts/quick_validate.py skills/.experimental/my-skill
```

### Step 6: Create a Pull Request

```bash
git add .
git commit -m "Add my-skill to experimental"
git push origin add-my-skill
```

Go to GitHub and create a Pull Request.

## Security

If you discover a vulnerability: email **security@openai.com**. Do not publish vulnerabilities in public issues.

## The Skill Journey

```
Your idea → experimental → (review) → curated → (possibly) system
```

## Summary

- Contributing starts with a fork and Pull Request
- New skills go into `.experimental`
- Follow community values
- Good experimental skills may be promoted to curated
- Security concerns go to security@openai.com
