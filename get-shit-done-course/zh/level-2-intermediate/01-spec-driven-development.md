---
title: "规范驱动开发"
level: 2
lesson: 1
language: zh
tags: [gsd, spec-driven, 需求]
---

# 规范驱动开发

## 介绍

GSD 建立在规范驱动开发原则上：先写规范，再写代码。不是"给我做个网站"，而是结构化的需求、路线图和计划。

## 操作指南

### 规范结构

GSD 自动创建：

1. **PROJECT.md** — 高层愿景
2. **REQUIREMENTS.md** — 具体需求，分为 v1/v2/范围外
3. **ROADMAP.md** — 与需求对应的阶段

### 工作流程

```
你的想法 → 提问 → 研究 → 需求 → 路线图 → 计划 → 代码
```

每一步都缩小不确定性。到写代码时，AI 确切知道该做什么。

### XML 格式的计划

```xml
<task type="auto">
  <name>创建登录端点</name>
  <files>src/api/auth/login.ts</files>
  <action>
    使用 jose 处理 JWT。
    验证凭据。
    返回 httpOnly cookie。
  </action>
  <verify>curl POST /api/auth/login → 200 + cookie</verify>
  <done>有效凭据 → cookie，无效 → 401</done>
</task>
```

## 示例

```
/gsd:new-project

> 我想要一个带团队、看板和 Slack 集成的
> 任务管理 SaaS。

GSD 创建：
- 包含愿景的 PROJECT.md
- 包含 ~15-20 个具体需求的 REQUIREMENTS.md
- 包含 4-6 个阶段的 ROADMAP.md
```

## 总结

- 规范驱动 = 代码前先写规范
- GSD 自动生成 PROJECT、REQUIREMENTS、ROADMAP
- 每个计划是带任务和验证的 XML 结构
- 在写代码前消除不确定性
