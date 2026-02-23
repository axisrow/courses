---
title: "Production Deployment"
weight: 13
bookToc: true
---

# Production Deployment

## From Script to Service

Moving a CrewAI project to production requires handling reliability, security, and scalability.

## CrewAI Deploy

CrewAI offers a deployment platform:

```bash
crewai deploy create
crewai deploy push
crewai deploy status
```

This packages your crew and deploys it as an API endpoint.

## Docker Deployment

Create a `Dockerfile`:

```dockerfile
FROM python:3.12-slim

WORKDIR /app
COPY . .
RUN pip install crewai 'crewai[tools]'

CMD ["python", "main.py"]
```

```bash
docker build -t my-crew .
docker run -e OPENAI_API_KEY=sk-... my-crew
```

## API Wrapper with FastAPI

```python
from fastapi import FastAPI
from crewai import Crew

app = FastAPI()

@app.post("/run")
async def run_crew(topic: str):
    # Define your crew here or import it
    crew = create_crew(topic)
    result = crew.kickoff()
    return {"result": str(result)}
```

```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

## Environment Management

Never hardcode API keys. Use:

```python
import os
from dotenv import load_dotenv

load_dotenv()
api_key = os.getenv("OPENAI_API_KEY")
```

## Production Checklist

- ✅ API keys in environment variables, not in code
- ✅ Error handling around `crew.kickoff()`
- ✅ Logging for monitoring
- ✅ Rate limiting for API endpoints
- ✅ Timeouts for long-running tasks
- ✅ `max_iter` set on all agents
- ✅ Health check endpoint
- ✅ Cost monitoring (LLM API usage)

## Scaling

- Run multiple crew instances behind a load balancer
- Use async execution for non-blocking tasks
- Cache common results to reduce API calls
- Monitor token usage to control costs

## Summary

Deploy with CrewAI's built-in tools, Docker, or wrap in a FastAPI service. Always secure API keys, add error handling, and monitor costs.

---

**Next:** Performance optimization.
