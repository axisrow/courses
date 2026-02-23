---
title: "第一次运行"
level: 1
lesson: 3
language: zh
tags: [gsd, 首次运行, new-project]
---

# 第一次运行

## 介绍

安装 GSD 后，第一步是创建项目。`/gsd:new-project` 命令启动完整的初始化流程。

## 操作指南

### 1. 启动 Claude Code

```bash
claude --dangerously-skip-permissions
```

> `--dangerously-skip-permissions` 标志是 GSD 推荐的——否则你需要确认每个小操作。

### 2. 创建项目

```
/gsd:new-project
```

系统经过 4 个阶段：
1. **提问** — 询问你的想法、目标、约束
2. **研究** — 启动并行代理调查领域
3. **需求** — 确定 v1、v2 和范围外的内容
4. **路线图** — 创建与需求对应的阶段

### 3. 批准路线图

创建路线图后，GSD 会展示给你。批准后就可以开始构建。

## 创建的文件

```
.planning/
├── PROJECT.md        # 项目愿景
├── REQUIREMENTS.md   # v1/v2 需求
├── ROADMAP.md        # 阶段路线图
├── STATE.md          # 当前状态
└── research/         # 研究结果
```

## 示例

```
/gsd:new-project

> 我想构建一个带 markdown 编辑器、GitHub 认证
> 和 Vercel 部署的博客平台。
```

## 总结

- `/gsd:new-project` 是任何项目的入口
- 系统自动提出正确的问题
- 在 `.planning/` 中创建结构
- 在开始工作前批准路线图
