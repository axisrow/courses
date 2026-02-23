---
title: "Building Custom Tools"
weight: 11
bookToc: true
---

# Building Custom Tools

## Why Custom Tools?

Built-in tools cover common cases. But your project may need tools that call your own API, query your database, or process data in a specific way.

## Creating a Custom Tool

```python
from crewai.tools import BaseTool
from pydantic import Field

class WeatherTool(BaseTool):
    name: str = "Weather Lookup"
    description: str = "Get current weather for a city. Input: city name."

    def _run(self, city: str) -> str:
        # In real code, call a weather API here
        return f"The weather in {city} is 22°C and sunny."
```

## Using Your Custom Tool

```python
weather = WeatherTool()

travel_agent = Agent(
    role="Travel Advisor",
    goal="Help plan trips with weather info",
    backstory="You are a helpful travel planner.",
    tools=[weather]
)
```

## Tool with API Calls

```python
import requests
from crewai.tools import BaseTool

class StockPriceTool(BaseTool):
    name: str = "Stock Price"
    description: str = "Get the current stock price. Input: ticker symbol (e.g., AAPL)."

    def _run(self, ticker: str) -> str:
        response = requests.get(f"https://api.example.com/stock/{ticker}")
        if response.ok:
            data = response.json()
            return f"{ticker}: ${data['price']}"
        return f"Could not fetch price for {ticker}"
```

## Using the @tool Decorator

A simpler approach for quick tools:

```python
from crewai.tools import tool

@tool("Calculator")
def calculator(expression: str) -> str:
    """Evaluate a math expression. Input: a math expression like '2 + 2'."""
    try:
        return str(eval(expression))
    except Exception as e:
        return f"Error: {e}"
```

## Tool Best Practices

1. **Clear name and description** — the agent uses these to decide when to call the tool
2. **Handle errors** — always return a string, even on failure
3. **Keep tools focused** — one tool, one purpose
4. **Test independently** before giving to an agent

## Summary

Custom tools let you extend CrewAI with any functionality. Use `BaseTool` class or `@tool` decorator. Write clear descriptions so agents know when to use them.

---

**Next:** Integrating different LLM providers.
