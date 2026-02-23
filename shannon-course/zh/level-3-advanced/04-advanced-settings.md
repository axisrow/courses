---
title: "高级设置"
weight: 4
bookToc: true
---

# 高级设置

## 简介

Shannon的高级功能：替代提供商、工作空间管理和优化。

## 路由模式：替代AI提供商

```bash
# 在.env中
OPENAI_API_KEY=sk-...
ROUTER_DEFAULT=openai,gpt-5.2

# 或通过OpenRouter
OPENROUTER_API_KEY=sk-or-...
ROUTER_DEFAULT=openrouter,google/gemini-3-flash-preview
```

```bash
./shannon start URL=https://app.com REPO=app ROUTER=true
```

> ⚠️ 实验性功能。质量取决于模型。某些模型可能在早期阶段就失败。

## 工作空间管理

```bash
./shannon workspaces                    # 列出所有
./shannon start ... WORKSPACE=q1-audit  # 命名工作空间
# 通过重用相同的工作空间名称恢复中断的测试
```

每个智能体通过git提交进行检查点，因此恢复从干净状态开始。

## Temporal Web UI

打开`http://localhost:8233`进行详细监控：工作流状态、智能体进度、时间、错误。

## 成本优化

- 典型运行：在Claude 4.5 Sonnet上约$50
- 路由模式使用更便宜的模型以质量换成本
- 工作空间节省资金：失败时无需重新开始

## Windows提示

- 使用WSL2获得最佳兼容性
- 将Shannon目录添加到Windows Defender排除项（PoC代码会触发误报）

## 总结

- 路由模式允许尝试其他AI模型
- 工作空间组织和恢复测试
- Temporal UI提供详细监控
- 模型选择影响成本和质量
