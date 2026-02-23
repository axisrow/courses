---
title: "团队协作"
weight: 14
bookToc: true
---

# 团队协作

## 团队工作

Windsurf 支持团队工作流。

## Git 集成

### 基本流程
1. **暂存更改** — 在 Source Control 中点击文件旁的 `+`
2. **提交** — 写提交信息并点击 ✓
3. **Push/Pull** — 与远程同步

### AI 提交信息
1. 暂存更改
2. 点击提交信息框中的 **AI 图标**
3. 审查并编辑生成的信息
4. 提交

## 用 AI 做代码审查

创建 Pull Request 前：
1. 让 Cascade："审查我的更改，找出潜在问题"
2. 修复发现的问题
3. 让 Cascade："为这些更改写 PR 描述"

## 共享设置

保持团队一致性：

```json
// .vscode/settings.json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.tabSize": 2
}
```

将此文件提交到仓库。

## 用 AI 结对编程

Windsurf 作为"第三个团队成员"：
- 一人编码，另一人用 Cascade 审查
- 用 Cascade 解释队友写的不熟悉的代码
- 用 Cascade 帮助新成员熟悉代码库

## Codeium Teams

团队计划包括：
- 统一计费
- 管理控制
- 使用分析
- 自定义 AI 模型设置

详情访问 [codeium.com](https://codeium.com)。

## 练习

在项目中设置共享的 `.vscode/settings.json`，用 AI 生成提交信息一周。
