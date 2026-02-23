---
title: "OSS 取证调查"
weight: 3
bookToc: true
---

## OSS 取证调查

### 什么是 OSS 取证？

RAPTOR 的 OSS 取证模块调查**公开 GitHub 仓库**，寻找供应链攻击、后门或可疑活动的证据。

### `/oss-forensics` 命令

```
/oss-forensics
```

### 证据收集来源

RAPTOR 从多个来源收集证据:

1. **GH Archive** — 所有公开 GitHub 事件的不可变历史数据，可通过 BigQuery 查询
2. **GitHub API** — 仓库当前状态
3. **Wayback Machine** — 网页的历史快照
4. **本地 Git** — 直接仓库分析

### 调查流程

取证模块使用**多代理架构**:

1. **证据收集阶段** — 专门的调查员并行收集数据
2. **IOC 提取** — 自动从供应商报告中提取入侵指标
3. **证据验证** — 与原始不可变来源严格校验
4. **假设形成** — AI 驱动的假设生成与迭代改进
5. **取证报告** — 详细时间线、归因分析和 IOC

### 恢复已删除内容

最强大的功能之一:RAPTOR 可以恢复**已删除内容**:
- 已删除的提交（如果知道 SHA 仍可访问）
- 已删除的 issue 和评论（通过 GH Archive）
- 修改过的仓库描述（通过 Wayback Machine）

### BigQuery 设置

```bash
export GOOGLE_APPLICATION_CREDENTIALS=/path/to/service-account.json
```

### 真实案例

XZ Utils 后门（CVE-2024-3094）是一个完美的例子，RAPTOR 的取证工具可以帮助调查攻击的时间线和涉及的账户。

### 核心要点

OSS 取证是 RAPTOR 的调查部门。它将 GitHub 仓库变成犯罪现场，提供基于证据的供应链攻击分析。
