---
title: "长时间运行的工作流"
weight: 4
bookToc: true
---

# 长时间运行的工作流

## 什么是长时间工作流？

某些任务需要数小时甚至数天。CodeMachine 专为此设计。

## 持久化

CodeMachine 自动保存工作流状态。中断后可以从中断处继续。

### 如何恢复

在同一项目文件夹中再次运行 `codemachine`。

## 暂停和恢复

按 **P** 暂停。重启 CodeMachine 继续。

## executeOnce 策略

```javascript
steps: [
  resolveStep('requirements', { executeOnce: true }),
  resolveStep('architecture', { executeOnce: true }),
  resolveStep('implementation'),
  resolveModule('testing', {
    loopSteps: 1,
    loopMaxIterations: 20,
  }),
],
```

## 信号

| 信号 | 快捷键 | 效果 |
|------|--------|------|
| 跳过 | Ctrl+S | 跳过当前步骤 |
| 暂停 | P | 暂停并保存 |
| 停止 | Escape | 停止 |
| 模式切换 | Shift+Tab | 切换模式 |

## 监控

- **Tab** — 时间线
- **H** — 历史
- 日志在 `.codemachine/logs/`

## 最佳实践

1. 设置步骤使用 `executeOnce`
2. 设置 `loopMaxIterations`
3. 监控日志
4. 先监督运行，再切换到自主

## 总结

- CodeMachine 支持数小时到数天的工作流
- 状态自动保存——随时恢复
- 使用 executeOnce、信号和监控

> **下一课：** 最佳实践。
