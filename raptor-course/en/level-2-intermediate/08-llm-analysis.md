---
title: "AI-Powered Vulnerability Analysis"
weight: 3
bookToc: true
---

## AI-Powered Vulnerability Analysis

### Why Use AI?

Traditional tools find potential issues but can't always tell you:
- Is this bug **really** exploitable?
- How **serious** is the impact?
- What's the best way to **fix** it?

RAPTOR uses large language models (LLMs) to answer these questions.

### The `/analyze` Command

```
/analyze
```

This runs LLM analysis **without** generating exploits or patches. It's 50% faster and cheaper than the full workflow.

### What the AI Examines

1. **Code context** — Reads surrounding code to understand the vulnerability
2. **Data flow** — Traces how malicious input reaches dangerous functions
3. **Exploitability** — Assesses how practical an attack would be
4. **Impact** — Estimates damage if exploited
5. **Recommendations** — Suggests specific fixes

### LLM Provider Configuration

RAPTOR supports multiple AI providers through **LiteLLM**:

- **Anthropic Claude** — Best overall quality
- **OpenAI GPT-4** — Strong alternative
- **Google Gemini** — Good quality
- **Ollama** — Free but lower quality for exploit generation

Configure in `litellm_config.yaml`:

```yaml
model_list:
  - model_name: claude-opus-4.5
    litellm_params:
      model: anthropic/claude-opus-4.5
      api_key: ${ANTHROPIC_API_KEY}
```

### Cost Management

RAPTOR tracks costs in real time. Set a budget to prevent surprise bills:

```python
config = LLMConfig(max_cost_per_scan=1.0)  # $1 limit per scan
```

Typical cost: approximately $0.03 per vulnerability analyzed.

### Key Takeaway

AI analysis transforms raw scan results into actionable intelligence. It tells you not just *what* the bug is, but *how dangerous* it is and *how to fix it*.
