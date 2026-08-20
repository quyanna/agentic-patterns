# Agentic AI patterns

Working implementations of the patterns agentic systems are built from, one pattern per notebook, instrumented so the mechanism stays visible instead of disappearing behind a framework.

Each notebook is my own run: my print statements, my variations, and notes on where the pattern breaks down. The patterns come from Ed Donner's [Complete Agentic AI Engineering Course](https://www.udemy.com/course/the-complete-agentic-ai-engineering-course/). The reference implementations live in [ed-donner/agents](https://github.com/ed-donner/agents), and nothing here is a copy of them.

## Patterns

| Pattern | Notebook | What it shows |
|---|---|---|
| Provider abstraction, evaluator-optimizer (LLM-as-judge) | [`2_lab2.ipynb`](2_lab2.ipynb) | One client interface driving eight different models through OpenAI-compatible endpoints, where the only things that change are `base_url` and `api_key`. A judge model then ranks the eight answers, which is the evaluation primitive agent evals are built on. |

### On trusting the judge

Evaluator-optimizer is one of the five workflow patterns: one model generates, a second scores the output, and the critique feeds back into the next attempt. It holds up only while the scorer is genuinely independent of the generator.

If the judge is also one of the competitors, it favours its own answer. Hiding which model produced which answer is a weaker fix than it looks. Panickssery et al. (NeurIPS 2024) found that GPT-4 and Llama 2 identify their own output well above chance, and that the strength of self-preference scales linearly with how well a model recognises itself. Anonymising removes the label, not the style. The real fixes are a held-out judge from a different model family, or a human pass.

> Panickssery, A. et al. *LLM Evaluators Recognize and Favor Their Own Generations.* NeurIPS 2024. https://arxiv.org/abs/2404.13076

## Ahead

Tool calling and the agent loop, context engineering, multi-agent handoffs, MCP servers and clients, and the frameworks compared side by side (OpenAI Agents SDK, CrewAI, LangGraph).

## Running these

Any OpenAI-compatible key works. These were run inside the course environment (`uv sync` in [ed-donner/agents](https://github.com/ed-donner/agents)) with keys in a local `.env`.
