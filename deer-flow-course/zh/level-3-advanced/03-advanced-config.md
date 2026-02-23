---
title: "高级配置"
weight: 3
bookToc: true
---

# 高级配置

## 简介

在本课中，我们将探索DeerFlow高级使用场景的所有配置选项。

## 完整config.yaml结构

```yaml
# AI模型
models:
  - name: gpt-4o
    display_name: GPT-4o
    use: langchain_openai:ChatOpenAI
    model: gpt-4o
    api_key: $OPENAI_API_KEY
    supports_vision: true

# 工具
tools:
  - name: web_search
    group: web
    use: src.community.tavily.tools:web_search_tool

# 沙箱
sandbox:
  use: src.sandbox.local:LocalSandboxProvider

# 记忆
memory:
  enabled: true
  injection_enabled: true
  storage_path: .deer-flow/memory.json
  max_facts: 100

# 摘要
summarization:
  enabled: true
  trigger:
    type: tokens
    threshold: 100000
```

## 环境变量

以`$`开头的值从环境变量中替换：

```yaml
api_key: $OPENAI_API_KEY
```

## 模型配置

### 支持Thinking的模型

```yaml
models:
  - name: deepseek-v3
    use: langchain_deepseek:ChatDeepSeek
    model: deepseek-chat
    api_key: $DEEPSEEK_API_KEY
    supports_thinking: true
```

### 支持Vision的模型

```yaml
models:
  - name: gpt-4o
    supports_vision: true   # 启用view_image工具
```

### 本地模型

```yaml
models:
  - name: ollama-llama
    display_name: Llama 3（本地）
    use: langchain_openai:ChatOpenAI
    model: llama3
    base_url: http://localhost:11434/v1
    api_key: ollama
```

## 摘要设置

按**token数量**、**消息数量**或上下文窗口**比例**触发：

```yaml
summarization:
  trigger:
    type: fraction
    threshold: 0.75   # 75%上下文使用时压缩
```

## MCP服务器配置

在`extensions_config.json`中配置。MCP配置可以通过API在运行时更新——LangGraph检测文件变化并重新加载工具。

## 运行时配置

某些参数可以按请求更改：

```json
{
  "configurable": {
    "thinking_enabled": true,
    "model_name": "gpt-4o",
    "is_plan_mode": true,
    "subagent_enabled": true
  }
}
```

## 总结

- `config.yaml`是中央配置文件
- 通过`$`前缀支持环境变量
- 模型支持thinking、vision和本地部署
- 摘要可按token、消息或比例触发
- MCP服务器可在运行时更新
- 运行时参数允许按请求更改行为
