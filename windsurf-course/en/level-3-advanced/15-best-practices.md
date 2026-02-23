---
title: "Performance & Best Practices"
weight: 15
bookToc: true
---

# Performance & Best Practices

## Performance Tips

### Keep Windsurf Fast
1. **Close unused tabs** — each tab uses memory
2. **Disable unused extensions** — fewer extensions = faster startup
3. **Exclude large folders** — add `node_modules`, `dist` to `.gitignore` and file excludes
4. **Use a modern machine** — 8 GB+ RAM recommended

### AI Response Speed
- Stable internet improves AI response time
- Smaller, focused prompts get faster answers
- Clear conversation history when it gets long

## Best Practices for AI Coding

### 1. Always Review AI Output
Never blindly accept generated code. Check for:
- Correctness — does it do what you asked?
- Security — no hardcoded secrets, SQL injection, etc.
- Style — does it match your project?

### 2. Write Good Prompts
- Be specific about what you want
- Mention the language, framework, and patterns
- Give examples when possible

### 3. Test Everything
AI-generated code needs tests just like human code:
- Ask Cascade to write tests
- Run tests after every AI change
- Use CI/CD to catch issues early

### 4. Use AI for the Right Tasks
**Great for:**
- Boilerplate code
- Tests and documentation
- Refactoring and formatting
- Explaining unfamiliar code

**Be careful with:**
- Security-critical logic
- Complex business rules
- Architecture decisions (use as advisor, not sole author)

### 5. Learn from the AI
Read the code it generates. You will learn new patterns, APIs, and techniques.

## Security Considerations

- Don't paste secrets into Cascade
- Review code for vulnerabilities before deploying
- Use `.env` files for sensitive data
- Check Codeium's data policy for your plan

## Summary

Windsurf is a powerful tool that makes you faster and more productive. Use it wisely:
- Let AI handle the repetitive work
- Focus your energy on design and logic
- Always review, test, and iterate

Congratulations on completing the course! 🎉
