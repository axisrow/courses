---
title: "Best Practices"
weight: 5
bookToc: true
---

# Best Practices

## Introduction

This lesson compiles recommendations for building high-quality skills.

## 1. Brevity Is Your Friend

The Codex context window is limited. Every skill shares it with the system prompt, conversation history, and other skills.

**Rule:** If Codex already knows it — don't write it.

## 2. The Description Is Everything

The description in the frontmatter is the only thing Codex always sees. If the description is vague, the skill won't trigger.

**Include:**
- What the skill does
- Specific triggers (words, scenarios)
- File types or tools involved

## 3. Progressive Disclosure

Don't cram everything into SKILL.md. Use three levels:

1. **Metadata** (~100 words) — always in context
2. **SKILL.md** (<5,000 words) — loaded on activation
3. **References** — loaded on demand

## 4. Degrees of Freedom

Choose detail level based on the task:

- **High freedom** — text instructions, many approaches valid
- **Medium freedom** — pseudocode, main pattern with variations
- **Low freedom** — specific scripts, strict sequence

**Rule:** The riskier the mistake, the lower the freedom.

## 5. Don't Create Extra Files

Do NOT add to a skill:
- README.md
- CHANGELOG.md
- INSTALLATION_GUIDE.md

Skills are read by AI agents, not humans.

## 6. Test Your Scripts

Every script in `scripts/` must be run and verified before publishing.

## 7. Naming

- Lowercase letters, digits, and hyphens only
- Short, verb-led phrases
- Use namespaces for tools: `gh-fix-ci`, `notion-meeting-intelligence`

## Quality Checklist

- [ ] SKILL.md has name and description in frontmatter
- [ ] Description thoroughly describes when to use the skill
- [ ] Body is concise and practical (under 500 lines)
- [ ] Scripts are tested
- [ ] No extra files (README, CHANGELOG)
- [ ] Name is in kebab-case
- [ ] `agents/openai.yaml` is filled in

## Summary

- Write concisely — the context window is limited
- Description is the main trigger
- Use progressive disclosure
- Don't create extra files
- Test all scripts
