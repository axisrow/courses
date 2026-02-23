---
title: "AI 模型与 LiteLLM"
weight: 8
bookToc: true
---

# AI 模型与 LiteLLM

## 选择你的"大脑"

Sentient 不会绑定你到某一个 AI 供应商。通过 **LiteLLM**，你可以使用几乎任何语言模型：

- **OpenAI** — GPT-4o、GPT-4、GPT-3.5
- **Google** — Gemini Pro、Gemini Flash
- **Anthropic** — Claude 3.5 Sonnet、Claude 3 Opus
- **本地模型** — 通过 **Ollama** 运行 Llama、Mistral、Qwen

## 什么是 LiteLLM？

LiteLLM 是 Sentient 和 AI 供应商之间的轻量级代理。它将请求转换为所选模型的正确格式，让你无需修改代码即可切换模型。

## 配置

配置文件在 `src/server/litellm-config.yaml`：

```yaml
model_list:
  - model_name: gpt-4o
    litellm_params:
      model: openai/gpt-4o
      api_key: sk-...
```

## 通过 Ollama 使用本地模型

为了最大化隐私：
1. 安装 [Ollama](https://ollama.com)。
2. 拉取模型：`ollama pull qwen2.5`
3. 将 LiteLLM 指向本地 Ollama 端点。

你的对话永远不会离开你的电脑。

## 如何选择模型？

| 需求 | 推荐 |
|---|---|
| 最高质量 | GPT-4o 或 Claude 3.5 Sonnet |
| 快速且便宜 | Gemini Flash 或 GPT-3.5 |
| 完全隐私（本地） | Qwen 2.5 或 Llama 3（通过 Ollama） |
| 平衡 | Gemini Pro |

## 小结

LiteLLM 赋予 Sentient 模型灵活性。你可以选择最适合需求的 AI 大脑——云端或本地，快速或强大。
