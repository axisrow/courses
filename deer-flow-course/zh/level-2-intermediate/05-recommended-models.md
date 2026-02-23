---
title: "推荐模型"
weight: 5
bookToc: true
---

# 推荐模型

## 简介

DeerFlow是**模型无关的**——它可以与任何支持OpenAI兼容API的AI模型配合使用。但并非所有模型都同样适合智能体任务。

## 智能体任务的关键要素

1. **长上下文窗口**（100K+ token）— 智能体处理大量信息
2. **推理能力** — 规划、任务分解、决策
3. **多模态** — 理解图表、截图、照片
4. **可靠的工具使用** — 稳定、正确的函数调用

## 推荐模型

### 首选

| 模型 | 提供商 | 上下文 | 推理 | 视觉 | 工具使用 |
|------|--------|--------|------|------|----------|
| GPT-4o | OpenAI | 128K | ✅ | ✅ | ✅✅ |
| Claude 3.5 Sonnet | Anthropic | 200K | ✅ | ✅ | ✅✅ |
| DeepSeek V3 | DeepSeek | 128K | ✅ | ✅ | ✅ |

### 经济型选择

| 模型 | 提供商 | 价格 |
|------|--------|------|
| GPT-4o-mini | OpenAI | 低 |
| Claude 3 Haiku | Anthropic | 低 |
| DeepSeek V3 | DeepSeek | 很低 |

## 配置示例

### OpenAI
```yaml
models:
  - name: gpt-4o
    display_name: GPT-4o
    use: langchain_openai:ChatOpenAI
    model: gpt-4o
    api_key: $OPENAI_API_KEY
    supports_vision: true
```

### Anthropic
```yaml
models:
  - name: claude-sonnet
    display_name: Claude 3.5 Sonnet
    use: langchain_anthropic:ChatAnthropic
    model: claude-3-5-sonnet-20241022
    api_key: $ANTHROPIC_API_KEY
    supports_vision: true
```

### 本地模型
```yaml
models:
  - name: local-model
    display_name: 本地LLM
    use: langchain_openai:ChatOpenAI
    model: my-model
    base_url: http://localhost:8080/v1
    api_key: not-needed
```

## 按任务选择模型

| 任务 | 推荐 |
|------|------|
| 研究 | GPT-4o、Claude Sonnet |
| 代码生成 | GPT-4o、DeepSeek V3 |
| 图片分析 | GPT-4o（supports_vision） |
| 简单任务 | GPT-4o-mini、DeepSeek V3 |
| 长对话 | Claude Sonnet（200K上下文） |

## 总结

- DeerFlow适用于任何OpenAI兼容模型
- 智能体任务最重要的是：长上下文、推理和工具使用
- GPT-4o和Claude Sonnet是首选
- DeepSeek V3是优秀的经济型选择
- 可通过OpenAI兼容API连接本地模型

🎉 第2级完成！继续第3级，深入了解DeerFlow的架构。
