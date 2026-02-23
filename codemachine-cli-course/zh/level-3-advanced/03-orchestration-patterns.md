---
title: "编排模式"
weight: 3
bookToc: true
---

# 编排模式

## 自动化光谱

```
完全交互 ←──────────────────→ 完全自主
 （你驱动）     （混合）         （AI 驱动）
```

## 模式 1：人在回路中

每个步骤需要人工批准。用于关键任务。

```javascript
export default {
  autonomousMode: 'never',
  steps: [
    resolveStep('planner'),
    resolveStep('implementer'),
    resolveStep('reviewer'),
  ],
};
```

## 模式 2：受监督自动化

大部分自动，关键步骤暂停审查。

```javascript
export default {
  autonomousMode: 'always',
  steps: [
    resolveStep('researcher'),
    resolveStep('implementer'),
    resolveStep('reviewer', { interactive: true }),  // 暂停
    resolveStep('deployer'),
  ],
};
```

## 模式 3：完全自动化

无需人工干预。用于已验证的工作流。

## 模式 4：迭代优化

用模块循环直到达到质量标准。

```javascript
steps: [
  resolveStep('implementer'),
  resolveModule('quality-gate', {
    loopSteps: 1,
    loopMaxIterations: 5,
  }),
],
```

## 模式 5：并行团队

```javascript
subAgentIds: ['frontend-dev', 'backend-dev', 'qa-engineer'],
```

## 选择模式

| 模式 | 信任度 | 速度 | 控制 |
|------|--------|------|------|
| 人在回路 | 低 | 慢 | 最大 |
| 受监督 | 中 | 中 | 平衡 |
| 完全自动 | 高 | 快 | 最小 |
| 迭代优化 | 中 | 可变 | 质量 |
| 并行团队 | 高 | 最快 | 分布式 |

## 总结

- 根据信任度和需求选择模式
- 从交互开始，逐步走向自主
- 在一个工作流内混合模式
- 循环用于质量保证

> **下一课：** 长时间运行的工作流。
