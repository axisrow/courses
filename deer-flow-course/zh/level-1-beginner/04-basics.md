---
title: "基础概念"
weight: 4
bookToc: true
---

# 基础概念

## 简介

现在您已经尝试了DeerFlow，让我们来理解核心概念，学会更有效地使用系统。

## 文件系统结构

DeerFlow使用虚拟文件系统。每个会话（对话）都有自己的文件夹集：

```
/mnt/user-data/
├── uploads/      ← 您上传的文件存放于此
├── workspace/    ← 智能体的工作目录
└── outputs/      ← 最终交付物
```

> **虚拟文件系统**是存在于容器（沙箱）内部的文件夹集合。它与您计算机上的文件是隔离的。

## 智能体工具

| 工具 | 说明 |
|------|------|
| `web_search` | 互联网搜索 |
| `web_fetch` | 加载网页内容 |
| `bash` | 运行终端命令 |
| `read_file` | 读取文件 |
| `write_file` | 创建和写入文件 |
| `str_replace` | 替换文件中的文本 |
| `ls` | 列出文件夹内容 |
| `present_files` | 向用户展示输出文件 |
| `view_image` | 查看图片 |

智能体会自动选择使用哪些工具——您只需描述任务。

## 配置：config.yaml

主配置文件是项目根目录中的`config.yaml`：

### 模型

```yaml
models:
  - name: gpt-4o
    display_name: GPT-4o
    use: langchain_openai:ChatOpenAI
    model: gpt-4o
    api_key: $OPENAI_API_KEY   # $表示值来自环境变量
```

### 沙箱

```yaml
sandbox:
  use: src.sandbox.local:LocalSandboxProvider    # 本地
  # 或
  use: src.community.aio_sandbox:AioSandboxProvider  # Docker
```

## 技能

**技能**是扩展智能体能力的专门指令。内置技能包括：研究、报告生成、幻灯片创建、网页和图片生成。

技能采用**渐进式加载**——仅在当前任务需要时才加载。

## 扩展：extensions_config.json

此文件通过**MCP**（Model Context Protocol）管理额外工具——这是将外部工具连接到AI智能体的标准。

## 实时输出

DeerFlow通过**SSE**（Server-Sent Events）实时显示结果。您可以看到哪些工具正在被调用、中间结果和子智能体进度。

## 总结

- DeerFlow为每个会话使用虚拟文件系统
- 智能体自动选择所需工具
- 设置存储在`config.yaml`和`extensions_config.json`中
- 技能扩展智能体的能力
- 结果实时显示
