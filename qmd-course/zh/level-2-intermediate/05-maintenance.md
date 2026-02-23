---
title: "索引维护"
weight: 10
bookToc: true
---

# 索引维护

## 更新索引

```sh
# 重新索引所有集合
qmd update

# 先 git pull 再索引
qmd update --pull
```

## 检查状态

```sh
qmd status
```

## 清理

```sh
qmd cleanup
```

删除孤立数据，随时可安全运行。

## 命名索引

```sh
qmd --index work collection add ~/work/docs --name work-docs
qmd --index work embed
qmd --index work search "季度报告"
```

## 数据存储

- **索引数据库**：`~/.cache/qmd/index.sqlite`
- **AI 模型**：`~/.cache/qmd/models/`

完全重置：删除 `~/.cache/qmd/` 目录。

## 建议

1. **每天运行 `qmd update`** — 在工作日开始时
2. **使用 `--pull`** — 如果文档在 git 仓库中
3. **大量更改后运行 `qmd embed`**
4. **定期检查 `qmd status`**

## 中级阶段总结

- ✅ 不同的输出格式
- ✅ 添加上下文提高搜索质量
- ✅ 生成和管理嵌入向量
- ✅ 通过 MCP 与 AI 代理集成
- ✅ 索引维护和故障排除

**下一阶段**：高级查询语法、混合搜索原理、HTTP 传输和性能优化。
