---
title: "Testing Skills"
weight: 3
bookToc: true
---

# Testing Skills

## Introduction

Testing is a critical step in skill creation. A well-tested skill works reliably and predictably.

## Step 1: Validate Structure

Run `quick_validate.py`:

```bash
python scripts/quick_validate.py ./my-skill
```

It checks: SKILL.md presence, YAML frontmatter, required fields, naming rules.

## Step 2: Test Scripts

Run every script in `scripts/` and verify:

```bash
python scripts/my_script.py --help
python scripts/my_script.py test_data.csv
python scripts/my_script.py empty.csv
```

Check that: no crashes, output matches expectations, edge cases handled.

## Step 3: Test in Codex

Install the skill locally and verify in real conditions:

```bash
cp -r ./my-skill ~/.codex/skills/
```

Check: Does it trigger on the right requests? Does it execute correctly? No false positives?

## Step 4: Evaluations

Some curated skills include `evaluations/` with JSON files for automated testing:

```json
{
  "prompt": "Prepare meeting notes",
  "expected_skill": "notion-meeting-intelligence",
  "expected_output_contains": ["template", "agenda"]
}
```

## Step 5: Iterate

1. Use the skill on real tasks
2. Notice issues
3. Update SKILL.md and scripts
4. Test again

## Testing Checklist

- [ ] `quick_validate.py` passes
- [ ] All scripts run correctly
- [ ] Skill triggers on the right requests
- [ ] No false positives
- [ ] Edge cases handled
- [ ] Tested on real tasks

## Summary

- Start with structural validation via `quick_validate.py`
- Test every script manually
- Verify the skill in real Codex usage
- Iterate based on experience
