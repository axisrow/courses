---
title: "理解结果"
weight: 5
bookToc: true
---

# 理解结果

## 简介

Shannon完成了测试——现在让我们学习如何阅读报告以及如何处理它。

## 输出结构

```
audit-logs/{hostname}_{sessionId}/
├── session.json          # 指标和会话数据
├── agents/               # 每个代理的执行日志
├── prompts/              # 提示快照
└── deliverables/
    └── comprehensive_security_assessment_report.md   # 主报告
```

## 如何阅读报告

报告只包含**已证实的漏洞**。每个发现包括：

### 1. 漏洞描述
发现了什么以及它是什么类型（SQL注入、XSS、SSRF等）

### 2. 严重级别
- **Critical（危急）** — 可能窃取所有数据或完全控制系统
- **High（高）** — 严重问题，需要紧急修复
- **Medium（中）** — 问题存在但利用更困难
- **Low（低）** — 轻微风险

### 3. 概念验证（PoC）
最有价值的部分——可直接使用的代码或命令来重现攻击。

### 4. 修复建议
需要在代码中做什么更改来修复漏洞。

## 如何处理结果

1. **确定优先级** — 首先修复Critical和High
2. **重现** — 使用PoC验证漏洞
3. **修复** — 修改代码
4. **重新测试** — 再次运行Shannon确认修复

## 总结

- 主文件是`deliverables/`文件夹中的报告
- 每个发现包括描述、严重性、PoC和建议
- 报告中的所有漏洞都是已证实的（实际被利用过的）
- 首先修复Critical和High，然后重新运行测试
