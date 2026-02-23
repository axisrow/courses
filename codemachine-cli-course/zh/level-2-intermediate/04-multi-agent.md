---
title: "多代理编排"
weight: 4
bookToc: true
---

# 多代理编排

## 为什么需要多个代理？

就像专家团队比一个通才更好，多个 AI 代理能更高效地处理复杂任务。

## 子代理

子代理与主代理并行工作：

```javascript
// config/sub.agents.js
export default [
  {
    id: 'frontend-dev',
    name: 'Frontend Developer',
    mirrorPath: 'prompts/frontend-mirror.md',
  },
  {
    id: 'backend-dev',
    name: 'Backend Developer',
    mirrorPath: 'prompts/backend-mirror.md',
  },
];
```

### 在工作流中使用

```javascript
export default {
  name: 'Full Stack Builder',
  steps: [
    resolveStep('architect'),
    resolveStep('implementation'),
  ],
  subAgentIds: ['frontend-dev', 'backend-dev'],
};
```

## 并行执行

```
主代理（架构师）
    ├── 子代理：Frontend  ──→ 构建 UI
    └── 子代理：Backend   ──→ 构建 API
```

## 控制器

```javascript
export default {
  controller: controller('project-manager', {
    engine: 'claude',
  }),
  steps: [...],
};
```

## 混合引擎

```javascript
resolveStep('planning', { engine: 'claude' }),
resolveStep('coding', { engine: 'codex' }),
resolveStep('review', { engine: 'claude' }),
```

## 总结

- 子代理用于并行工作
- 控制器监督和决策
- 混合引擎发挥各自优势
- 并行执行节省时间

> **下一课：** 模块和循环。
