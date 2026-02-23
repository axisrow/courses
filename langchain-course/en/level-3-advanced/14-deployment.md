---
title: "Deployment and Production"
weight: 14
bookToc: true
---

# Deployment and Production

## LangServe — Deploy as API

LangServe turns any chain into a REST API:

```bash
pip install langserve[all] fastapi uvicorn
```

```python
from fastapi import FastAPI
from langserve import add_routes
from langchain_openai import ChatOpenAI
from langchain_core.prompts import ChatPromptTemplate

app = FastAPI(title="My LangChain API")

prompt = ChatPromptTemplate.from_template("Tell me about {topic}")
llm = ChatOpenAI(model="gpt-4o-mini")
chain = prompt | llm

add_routes(app, chain, path="/chat")

if __name__ == "__main__":
    import uvicorn
    uvicorn.run(app, host="0.0.0.0", port=8000)
```

Visit `http://localhost:8000/chat/playground/` for an interactive UI.

## Docker Deployment

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

## Production Checklist

- ✅ Use environment variables for API keys
- ✅ Add rate limiting
- ✅ Enable request logging and tracing (LangSmith)
- ✅ Set up error handling and fallbacks
- ✅ Use caching for repeated queries
- ✅ Monitor token usage and costs
- ✅ Add authentication to your API

## Caching

```python
from langchain_core.globals import set_llm_cache
from langchain_community.cache import SQLiteCache

set_llm_cache(SQLiteCache(database_path="cache.db"))
# Repeated queries will be served from cache
```

## Rate Limiting

```python
from langchain_core.rate_limiters import InMemoryRateLimiter

limiter = InMemoryRateLimiter(requests_per_second=1)
llm = ChatOpenAI(model="gpt-4o-mini", rate_limiter=limiter)
```

## Cloud Deployment Options

| Platform | Notes |
|----------|-------|
| AWS Lambda | Serverless, good for low traffic |
| Google Cloud Run | Containerized, auto-scaling |
| Azure Container Apps | Integrated with Azure OpenAI |
| Railway / Render | Simple deployment from Git |
| LangGraph Cloud | Managed hosting for LangGraph apps |

## Next Steps

In our final lesson, we'll explore multi-agent systems with LangGraph.
