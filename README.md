# Agentic AI patterns

Working implementations of the patterns agentic systems are actually built from — one pattern per notebook, instrumented so the mechanism is visible rather than hidden behind a framework.

Each notebook is my own run: my print statements, my variations, and notes on where the pattern breaks down. The patterns are drawn from Ed Donner's [Complete Agentic AI Engineering Course](https://www.udemy.com/course/the-complete-agentic-ai-engineering-course/); the reference implementations live in [ed-donner/agents](https://github.com/ed-donner/agents), and nothing here is a copy of them.

## Patterns

| Pattern | Notebook | What it shows |
|---|---|---|
| Provider abstraction · LLM-as-judge | [`2_lab2.ipynb`](2_lab2.ipynb) | One client interface driving eight different models through OpenAI-compatible endpoints — only `base_url` and `api_key` change. A judge model then ranks the eight answers, which is the same evaluation primitive agent evals are built on. |

## Ahead

Tool calling and the agent loop · context engineering · multi-agent handoffs · MCP servers and clients · agent frameworks compared (OpenAI Agents SDK, CrewAI, LangGraph)

## Running these

```bash
uv sync
cp .env.example .env   # add your provider keys
```
