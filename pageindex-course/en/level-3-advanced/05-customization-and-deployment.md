---
title: "Customization and Deployment"
weight: 5
bookToc: true
---

# Customization and Deployment

## Tailoring PageIndex to Your Needs

PageIndex is designed to be customizable. This lesson covers how to fine-tune it for specific use cases and deploy it in production.

## Configuration Tuning

### Model Selection

The default model is `gpt-4o-2024-11-20`, but you can use any OpenAI-compatible model:

```python
result = page_index("document.pdf", model="gpt-4o-mini")
```

Trade-offs:
- **GPT-4o**: Best accuracy, higher cost, slower
- **GPT-4o-mini**: Good accuracy, lower cost, faster
- **Other models**: May work via compatible APIs

### Node Size Parameters

Control how detailed the tree becomes:

```python
result = page_index(
    "document.pdf",
    max_page_num_each_node=5,     # Smaller = more detailed tree
    max_token_num_each_node=10000  # Smaller = more subdivisions
)
```

- **Smaller values**: More detailed tree, better for large documents, more API calls
- **Larger values**: Coarser tree, fewer API calls, faster processing

### TOC Detection Range

```python
result = page_index(
    "document.pdf",
    toc_check_page_num=30  # Check more pages for TOC
)
```

Increase this for documents where the TOC appears later (e.g., after a long preface).

## Deployment Options

### Option 1: Self-Hosted (Local)

Run PageIndex on your own machine or server:

**Pros**: Full control, data stays on your infrastructure, no usage limits
**Cons**: Need your own API key, manage infrastructure

### Option 2: Cloud API

Use the hosted PageIndex API:

**Pros**: No setup required, managed infrastructure, always up-to-date
**Cons**: Data leaves your network, usage-based pricing

### Option 3: Enterprise Deployment

For large organizations:
- Private cloud or on-premises deployment
- Custom model integration
- Volume pricing
- Dedicated support

## Production Considerations

### Cost Management

Each document processing requires multiple LLM API calls. To manage costs:

1. **Cache results** — Store generated trees for reuse
2. **Use smaller models** for initial passes, larger models for verification
3. **Set appropriate node size limits** — larger nodes mean fewer API calls
4. **Batch processing** — Process documents during off-peak hours

### Performance Optimization

- **Concurrency**: PageIndex already uses async processing; ensure your system supports concurrent API calls
- **Caching**: Store tree structures so you don't reprocess the same document
- **Preprocessing**: Pre-generate trees for document libraries; tree search is fast once the tree exists

### Error Handling

In production, handle these scenarios:
- API rate limits (implement exponential backoff)
- Documents with no useful structure (provide a fallback response)
- Very large documents (set appropriate timeouts)
- Corrupted or password-protected PDFs (validate before processing)

## Extending PageIndex

You can extend the system by:

1. **Custom post-processing** — Add your own fields to the tree nodes
2. **Alternative models** — Adapt the API functions to work with non-OpenAI models
3. **Domain-specific prompts** — Modify the prompts for better results in your domain
4. **Integration layers** — Build wrappers for your specific use case

## Summary

PageIndex can be customized through configuration parameters, deployed in multiple ways (local, cloud, enterprise), and extended for specific use cases. Production deployments should consider cost management, caching, and robust error handling.
