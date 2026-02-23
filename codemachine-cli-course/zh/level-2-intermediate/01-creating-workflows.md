---
title: "创建你的第一个工作流"
weight: 1
bookToc: true
---

# 创建你的第一个工作流

## 使用 Ali 构建

Ali 是内置的工作流构建器，引导你完成：

1. **设置** — 描述项目
2. **头脑风暴** — 定义目标
3. **工作流定义** — 结构化步骤
4. **代理** — 配置 AI 工作者
5. **提示词** — 编写指令
6. **生成** — 创建最终文件

## 手动创建

需要三样东西：

### 1. 代理配置（`config/main.agents.js`）

```javascript
export default [
  {
    id: 'researcher',
    name: 'Research Agent',
    description: '收集信息',
    promptPath: '.codemachine/prompts/research.md',
  },
  {
    id: 'implementer',
    name: 'Implementation Agent',
    description: '编写代码',
    promptPath: '.codemachine/prompts/implement.md',
  },
];
```

### 2. 提示词文件

```markdown
---
name: '研究阶段'
description: '收集需求和上下文'
---

# 研究阶段

## 步骤目标：
通过分析代码库和需求来理解需要构建什么。

## 指令序列
### 1. 阅读项目规格说明
### 2. 探索现有代码库
### 3. 为下一步总结发现
```

### 3. 工作流文件

```javascript
export default {
  name: 'My First Workflow',
  steps: [
    resolveStep('researcher'),
    resolveStep('implementer'),
  ],
};
```

## 运行

```bash
codemachine
```

## 总结

- 用 Ali 引导式创建
- 或手动创建配置、提示词和工作流文件
- 用 `codemachine` 运行

> **下一课：** 编写有效的提示词。
