---
title: "Experimental Skills"
weight: 1
bookToc: true
---

# Experimental Skills

## Introduction

Besides curated skills, the openai/skills repository has an `.experimental` folder. It contains skills that have not been fully reviewed but may already be useful.

## Differences from Curated

| | Curated | Experimental |
|---|---|---|
| Review | Verified by OpenAI | Not fully reviewed |
| Stability | High | May change |
| Support | Official | Community |
| Folder | `.curated` | `.experimental` |

## Installing an Experimental Skill

Specify the `.experimental` folder explicitly:

```
$skill-installer install the create-plan skill from the .experimental folder
```

Or provide the full GitHub URL:

```
$skill-installer install https://github.com/openai/skills/tree/main/skills/.experimental/create-plan
```

## Listing Experimental Skills

```
$skill-installer show experimental skills
```

## Warnings

- Experimental skills may be unstable
- They may be removed or promoted to curated
- Use at your own risk
- If you like a skill — help improve it by contributing

## Summary

- Experimental skills are community skills in development
- Installed via skill-installer with the `.experimental` folder
- Less stable than curated but potentially very useful
