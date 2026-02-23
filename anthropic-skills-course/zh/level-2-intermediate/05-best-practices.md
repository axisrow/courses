---
title: "最佳实践"
weight: 5
bookToc: true
---

# 最佳实践

## 简介

创建有效技能的建议。

## 描述质量

```yaml
# ❌ 差
description: Helps write stuff

# ✅ 好
description: >
  Creates structured technical documentation including API references.
  Use when user needs to write technical docs.
```

## 五条规则

1. **单一任务** — 一个技能做好一件事
2. **具体指令** — 无歧义
3. **示例** — 展示预期输出
4. **测试** — 用多种输入验证
5. **迭代** — 根据结果改进

## 文件夹结构

```
my-skill/
├── SKILL.md
├── scripts/
├── examples/
├── reference/
└── LICENSE.txt
```

## 总结

- 好的描述 = 正确的激活
- 带示例的结构化指令是关键
- 一个技能 = 一个任务
- 持续测试和改进
