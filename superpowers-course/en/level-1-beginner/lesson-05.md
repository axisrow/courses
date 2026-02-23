---
title: "TDD Approach in Superpowers"
level: 1
lesson: 5
lang: en
---

# TDD Approach in Superpowers

## Introduction

How Superpowers implements test-driven development: RED → GREEN → REFACTOR.

## What is TDD

Test-Driven Development — an approach where **tests are written before code**:

1. **RED** — write a test, see it fail
2. **GREEN** — write minimal code to pass
3. **REFACTOR** — improve code without breaking tests

## How Superpowers Enforces TDD

Superpowers **forces** the agent to follow TDD. The `test-driven-development` skill activates automatically:

- Agent **cannot** write code before tests
- If code is written first — the skill forces deletion and starting with a test
- Each RED-GREEN-REFACTOR cycle ends with a commit

## Example Cycle

### RED
```typescript
describe('Calculator', () => {
  it('should add two numbers', () => {
    const calc = new Calculator();
    expect(calc.add(2, 3)).toBe(5);
  });
});
```
Test fails: `Calculator is not defined` ✗

### GREEN
```typescript
export class Calculator {
  add(a: number, b: number): number {
    return a + b;
  }
}
```
Test passes ✓

### REFACTOR
Code is already clean — commit!

## Anti-patterns

| Anti-pattern | How Superpowers Helps |
|-------------|----------------------|
| Code without tests | Won't let you write code before tests |
| Too-large steps | Tasks are 2-5 minutes |
| Skipping RED phase | Requires seeing a failing test |
| Refactoring without tests | Tests already exist |

## Summary

- TDD is mandatory in Superpowers
- RED → GREEN → REFACTOR cycle for every task
- Agent cannot skip any phase
- Result: reliable code with full test coverage
