---
title: "Superpowers 中的 TDD 方法"
level: 1
lesson: 5
lang: zh
---

# Superpowers 中的 TDD 方法

## 简介

Superpowers 如何实现测试驱动开发：RED → GREEN → REFACTOR。

## 什么是 TDD

测试驱动开发 — **先写测试再写代码**的方法：

1. **RED** — 写测试，确认失败
2. **GREEN** — 写最少的代码使测试通过
3. **REFACTOR** — 改进代码，不破坏测试

## Superpowers 如何强制 TDD

Superpowers **强制**代理遵循 TDD。`test-driven-development` 技能自动激活：

- 代理**不能**在测试之前写代码
- 如果先写了代码 — 技能会强制删除并从测试开始
- 每个 RED-GREEN-REFACTOR 循环以提交结束

## 示例循环

### RED
```typescript
describe('Calculator', () => {
  it('should add two numbers', () => {
    const calc = new Calculator();
    expect(calc.add(2, 3)).toBe(5);
  });
});
```
测试失败 ✗

### GREEN
```typescript
export class Calculator {
  add(a: number, b: number): number {
    return a + b;
  }
}
```
测试通过 ✓

### REFACTOR
代码已经整洁 — 提交！

## 反模式

| 反模式 | Superpowers 如何帮助 |
|--------|---------------------|
| 没有测试的代码 | 不允许在测试之前写代码 |
| 步骤太大 | 任务限制在 2-5 分钟 |
| 跳过 RED 阶段 | 要求看到失败的测试 |
| 没有测试的重构 | 测试已经存在 |

## 总结

- TDD 是 Superpowers 的强制要求
- 每个任务都执行 RED → GREEN → REFACTOR
- 代理不能跳过任何阶段
- 结果：可靠的代码和完整的测试覆盖
