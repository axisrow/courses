---
title: "安装与设置"
weight: 3
bookToc: true
---

# 安装与设置

## 准备工作

安装 PageIndex 之前，请确保您有：

- **Python 3.8 或更新版本**
- **OpenAI API 密钥**（PageIndex 默认使用 GPT-4o）
- **一个 PDF 文档**用于测试

## 第一步：获取代码

从 GitHub 下载 PageIndex：

```bash
git clone https://github.com/VectifyAI/PageIndex.git
cd PageIndex
```

## 第二步：安装依赖

安装所需的 Python 包：

```bash
pip3 install --upgrade -r requirements.txt
```

## 第三步：设置 API 密钥

在 PageIndex 文件夹中创建 `.env` 文件，添加您的 OpenAI 密钥：

```bash
CHATGPT_API_KEY=your_openai_key_here
```

将 `your_openai_key_here` 替换为您从 [platform.openai.com](https://platform.openai.com) 获取的实际密钥。

## 第四步：处理您的第一个文档

运行以下命令处理 PDF 文档：

```bash
python3 run_pageindex.py --pdf_path /path/to/your/document.pdf
```

系统将会：
1. 读取您的 PDF
2. 检测是否有目录
3. 构建树结构
4. 将结果保存为 `./results/` 文件夹中的 JSON 文件

## 理解输出

输出是一个包含完整树结构的 JSON 文件，包括章节标题、页码范围、摘要和嵌套子章节。

## 常用配置选项

| 选项 | 默认值 | 说明 |
|------|-------|------|
| `--model` | gpt-4o-2024-11-20 | 使用的 AI 模型 |
| `--toc-check-pages` | 20 | 扫描目录的页数 |
| `--max-pages-per-node` | 10 | 拆分节点前的最大页数 |
| `--max-tokens-per-node` | 20000 | 拆分节点前的最大 token 数 |
| `--if-add-node-summary` | yes | 是否为每个章节生成摘要 |
| `--if-add-node-id` | yes | 是否为每个节点添加唯一 ID |

## Markdown 支持

PageIndex 也可以处理 Markdown 文件：

```bash
python3 run_pageindex.py --md_path /path/to/your/document.md
```

注意：Markdown 文件必须使用正确的标题层级（`#`、`##`、`###` 等）。

## 使用云服务

如果不想安装任何东西，可以通过以下方式使用 PageIndex：

- **聊天平台**：[chat.pageindex.ai](https://chat.pageindex.ai) — 上传文档并提问
- **API**：以编程方式集成到您的应用中
- **MCP**：与 Claude、Cursor 等 MCP 兼容工具配合使用

## 总结

设置 PageIndex 只需要 Python、一个 OpenAI API 密钥和几条命令。您可以在本地处理 PDF 或 Markdown 文档，也可以使用云服务获得更简单的体验。
