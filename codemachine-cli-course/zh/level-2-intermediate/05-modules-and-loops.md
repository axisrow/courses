---
title: "模块和循环"
weight: 5
bookToc: true
---

# 模块和循环

## 什么是模块？

模块是可以重复执行的特殊步骤，适合需要迭代的任务。

## 配置模块

```javascript
// config/modules.js
export default [
  {
    id: 'quality-check',
    name: 'Quality Checker',
    promptPath: 'prompts/quality-check.md',
    behavior: {
      type: 'loop',
      action: 'stepBack',
    },
  },
];
```

## 在工作流中使用

```javascript
steps: [
  resolveStep('planner'),
  resolveStep('coder'),
  resolveModule('quality-check', {
    loopSteps: 2,
    loopMaxIterations: 10,
    loopSkip: ['planner'],
  }),
],
```

### 工作原理

```
步骤 1：计划 → 步骤 2：编码 → 步骤 3：检查
                  ↑                    ↓
                  └──── 回退 ──────────┘
                    （如果发现问题）
```

## executeOnce 选项

```javascript
resolveStep('initial-setup', {
  executeOnce: true,  // 重启时不会重复
}),
```

## 文件夹 — 分组步骤

```javascript
...resolveFolder('preparation'),

...resolveFolder('implementation', {
  engine: 'codex',
  model: 'gpt-5',
}),
```

## 总结

- 模块是可循环的步骤
- 用 `loopSteps`、`loopMaxIterations`、`loopSkip` 控制循环
- `executeOnce` 用于一次性步骤
- `resolveFolder` 加载步骤组

> **恭喜！** 第二级完成。第三级将探索高级模式。
