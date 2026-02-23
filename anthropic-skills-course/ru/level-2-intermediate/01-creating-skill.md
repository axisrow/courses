---
title: "Создание своего навыка с нуля"
weight: 1
bookToc: true
---

# Создание своего навыка

## Введение

Создать навык просто: нужна папка с файлом `SKILL.md`. В этом уроке мы создадим навык пошагово.

## Шаг 1: Определите задачу

Перед созданием ответьте на вопросы:

- Какую задачу должен решать навык?
- Когда Claude должен его активировать?
- Какой результат ожидается?

## Шаг 2: Создайте структуру

```bash
mkdir code-reviewer
cd code-reviewer
```

## Шаг 3: Напишите SKILL.md

```markdown
---
name: code-reviewer
description: Reviews Python code for best practices, security vulnerabilities, and performance issues. Use when user asks to review Python code or audit code quality.
---

# Code Review Skill

You are a code reviewer specializing in Python. Follow this process:

## Review Process

1. **Read** the entire codebase first
2. **Security**: Check for SQL injection, XSS, hardcoded secrets
3. **Performance**: Look for N+1 queries, unnecessary loops
4. **Style**: Verify PEP 8 compliance
5. **Architecture**: Assess separation of concerns

## Output Format

For each issue found:
- 🔴 Critical — security vulnerabilities
- 🟡 Warning — performance or logic issues  
- 🔵 Info — style and improvement suggestions

## Example Review

Input: `eval(user_input)`

Output:
> 🔴 **Critical: Code Injection**
> `eval()` with user input allows arbitrary code execution.
> Fix: Use `ast.literal_eval()` or validate input explicitly.

## Guidelines
- Be constructive
- Provide fix examples
- Prioritize security over style
```

## Шаг 4: Протестируйте

Подключите навык и попросите Claude:

> «Проверь этот Python-код на проблемы»

## Использование skill-creator

В репозитории Anthropic есть мета-навык `skill-creator`, который помогает создавать новые навыки. Он проведёт вас через структурированный процесс.

## Итоги

- Навык — это папка с `SKILL.md`
- Начните с определения задачи и ожидаемого результата
- Пишите конкретные инструкции с примерами
- Используйте `skill-creator` для помощи
