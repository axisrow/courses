---
title: "输出格式"
weight: 6
bookToc: true
---

# 输出格式

## 为什么需要不同格式？

默认情况下 QMD 在终端显示彩色输出。但脚本和 AI 代理需要机器可读的格式。

## 可用格式

| 标志 | 格式 | 适用场景 |
|------|------|----------|
| *(默认)* | 彩色 CLI | 终端阅读 |
| `--json` | JSON | 脚本和 AI 代理 |
| `--files` | 文件列表 | 管道和工具集成 |
| `--csv` | CSV | 电子表格 |
| `--md` | Markdown | 文档和报告 |
| `--xml` | XML | 结构化数据交换 |

## 示例

```sh
# AI 用的 JSON
qmd search "认证" --json -n 10

# 文件列表
qmd query "错误处理" --all --files --min-score 0.4

# 带完整文本的 Markdown
qmd search "API 设计" --md --full

# 表格用的 CSV
qmd search "项目计划" --csv
```

## 控制结果数量

```sh
# 显示 10 条结果
qmd search "查询" -n 10

# 显示所有高于阈值的结果
qmd search "查询" --all --min-score 0.3
```

## 禁用颜色

```sh
NO_COLOR=1 qmd search "查询"
```

## 下一步

学习如何为集合添加上下文以提高搜索质量。
