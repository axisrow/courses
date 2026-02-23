---
title: "上下文工程"
weight: 2
bookToc: true
---

# 上下文工程

## 为什么上下文很重要

AI 代理在获得恰好需要的信息时表现最好——不多不少。

## 占位符

占位符将动态内容注入提示词：

```javascript
// config/placeholders.js
export default {
  userDir: {
    project_specs: 'inputs/specifications.md',
    api_docs: 'inputs/api-documentation.md',
  },
  packageDir: {
    step_completion: 'shared/step-completion.md',
  },
};
```

在提示词中使用：

```markdown
## 项目需求：
{project_specs}

## 完成后：
{step_completion}
```

## 上下文边界

```markdown
## 上下文边界：
- 仅读取 src/components/ 中的文件
- 不要修改 package.json
- 不要访问环境变量
```

## 步骤间传递上下文

每个步骤的输出自动作为下一步的上下文。

## 规格说明文件

```bash
codemachine --spec path/to/my-spec.md
```

## 最佳实践

1. **少即是多** — 只给需要的信息
2. **结构化输入** — 用 markdown 标题和列表
3. **明确边界** — 总是说明禁止访问的内容
4. **共享模板** — 通过占位符复用

## 总结

- 占位符注入动态内容
- 上下文边界保持代理专注
- 上下文在步骤间自动传递
- 给代理恰好需要的信息

> **下一课：** 编排模式。
