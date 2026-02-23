---
title: "最佳实践"
weight: 5
bookToc: true
---

# 最佳实践

## 设计原则

### 1. 从简单开始，逐步增加复杂度

从 2-3 步开始。测试。然后添加更多。

### 2. 一个代理，一个职责

✅ 好：`code-reviewer`、`security-auditor`、`test-writer`
❌ 坏：`do-everything-agent`

### 3. 像写食谱一样写提示词

```markdown
## 目标：检查 src/ 中的 JS 文件是否有安全漏洞。

## 指令：
### 1. 列出 src/ 中的 .js 和 .ts 文件
### 2. 检查每个文件：
   - SQL 注入
   - XSS 攻击
   - 硬编码凭据
### 3. 创建报告 output/security-report.md

## 成功：每个文件都有报告
## 失败：文件被跳过或报告缺失
```

### 4. 为任务选择正确的引擎

| 任务 | 引擎 |
|------|------|
| 写代码 | Codex |
| 代码审查 | Claude |
| 架构设计 | Claude |
| 测试 | Codex |

### 5. 版本控制你的工作流

用 Git 管理工作流。

## 常见工作流模板

### Bug 修复
```javascript
steps: [
  resolveStep('reproducer'),
  resolveStep('analyzer'),
  resolveStep('fixer'),
  resolveModule('verifier', { loopSteps: 1, loopMaxIterations: 5 }),
]
```

### 功能开发
```javascript
steps: [
  resolveStep('researcher'),
  resolveStep('architect'),
  resolveStep('implementer'),
  resolveStep('reviewer'),
],
subAgentIds: ['frontend-dev', 'backend-dev'],
```

## 故障排除

| 问题 | 解决方案 |
|------|----------|
| 代理跳过步骤 | 添加"强制"规则和编号 |
| 无限循环 | 设置 `loopMaxIterations` |
| 引擎错误 | 检查配置和覆盖 |
| 上下文太大 | 使用边界，拆分步骤 |

## 接下来？

- [官方文档](https://docs.codemachine.co)
- [Discord 社区](https://discord.gg/vS3A5UDNSq)
- [Reddit 社区](https://www.reddit.com/r/CodeMachine/)

## 总结

- 从简单开始
- 一个代理 = 一个任务
- 提示词 = 详细食谱
- 版本控制工作流
- 利用社区

> **恭喜！** 你完成了整个 CodeMachine CLI 课程。现在你已经掌握了构建强大 AI 工作流的知识。去创造吧！🚀
