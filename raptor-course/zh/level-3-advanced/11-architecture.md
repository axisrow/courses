---
title: "RAPTOR 架构深入解析"
weight: 1
bookToc: true
---

## RAPTOR 架构深入解析

### 多层设计

RAPTOR 使用**渐进式披露**架构——只加载需要的内容:

#### 第一层:Bootstrap（CLAUDE.md）
始终加载。包含核心决策系统和基本命令。

#### 第二层:Tier 1 技能
需要时自动加载:
- 对抗性思维
- 分析指导
- 恢复程序

#### 第三层:Tier 2 专家角色
按需加载。九个专业专家角色:

1. **Mark Dowd** — 深度代码审查
2. **Charlie Miller / Halvar Flake** — 二进制利用
3. **安全研究员** — 通用漏洞研究
4. **补丁工程师** — 安全代码修复
5. **渗透测试员** — 攻击性测试方法论
6. **模糊测试策略师** — 模糊测试优化
7. **二进制利用专家** — 底层利用
8. **CodeQL 数据流分析师** — 查询编写
9. **CodeQL 发现分析师** — 结果解读

#### 第四层:代理
自主代理，如**攻击性安全专家**。

### Python 执行层

```
raptor.py          → 统一启动器（CLI 入口点）
packages/          → 9 个安全能力包
  ├── autonomous/         → 完整工作流程编排
  ├── binary_analysis/    → 二进制逆向和分析
  ├── codeql/             → CodeQL 集成
  ├── exploit_feasibility/→ 可利用性评估
  ├── exploitability_validation/ → 验证引擎
  ├── fuzzing/            → AFL++ 集成
  ├── llm_analysis/       → LLM 驱动分析
  ├── recon/              → 侦察
  └── sca/                → 软件组成分析
core/              → 共享工具
engine/            → 规则和查询
```

### Token 预算

渐进式加载保持上下文高效:
- Bootstrap:约 360 个 token
- Tier 1:约 925 个 token
- 包含角色的完整加载:最多约 2,500 个 token

### 核心要点

RAPTOR 的架构是模块化和高效的。理解各层有助于你为每个任务使用正确的工具深度。
