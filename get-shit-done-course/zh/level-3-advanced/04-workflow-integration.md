---
title: "工作流集成"
level: 3
lesson: 4
language: zh
tags: [gsd, 集成, 工作流, ci-cd]
---

# 工作流集成

## 介绍

GSD 可以集成到现有工作流中：CI/CD、Docker、团队协作。

## 操作指南

### Docker 和 CI

对于容器化环境，使用非交互式安装：

```bash
# 在 Dockerfile 中
RUN npx get-shit-done-cc --claude --global

# 如果 ~ 不展开：
CLAUDE_CONFIG_DIR=/home/user/.claude npx get-shit-done-cc --global
```

### 团队的 Git 策略

对于团队工作，推荐使用 `phase` 或 `milestone` 策略：

```
/gsd:settings
> git.branching_strategy = phase
```

每个阶段创建一个分支，阶段完成时合并。

### 将 .planning/ 提交到 Git

默认情况下，GSD 提交 `.planning/`。好处：
- 决策历史
- 团队可见性
- 可重现性

禁用：`planning.commit_docs = false`。

### 安全性

保护敏感文件：

```json
{
  "permissions": {
    "deny": [
      "Read(.env)",
      "Read(.env.*)",
      "Read(**/*.pem)",
      "Read(**/*.key)"
    ]
  }
}
```

### 团队工作流

```
开发者 A: /gsd:new-project → 创建规范
团队:     审查 REQUIREMENTS.md 和 ROADMAP.md
开发者 A: /gsd:plan-phase 1 → 创建计划
开发者 B: /gsd:execute-phase 1 → 执行
开发者 A: /gsd:verify-work 1 → 验证
```

## 示例

```bash
# CI: 安装和执行
npx get-shit-done-cc --claude --global
claude --dangerously-skip-permissions << 'EOF'
/gsd:resume-work
/gsd:execute-phase 3
EOF
```

## 总结

- GSD 通过非交互式安装在 Docker 和 CI 中工作
- Git 策略 phase/milestone 用于团队工作
- .planning/ 在 git 中提供决策历史
- 通过 deny 列表保护敏感文件
