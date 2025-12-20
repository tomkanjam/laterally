---
title: "LLM evals for solo founders: what actually matters"
date: 2024-12-19
description: "A practical guide to LLM evaluation tools when you're building alone and can't afford to waste time on the wrong stack."
draft: true
---

![](/images/blog/llm-evals-solo-founder-header.svg)

I've spent more time than I'd like to admit evaluating evaluation tools. The irony isn't lost on me.

Here's what I learned so you don't have to repeat my mistakes.

## The problem

You're shipping LLM features. Sometimes they work. Sometimes they confidently produce garbage. You need to know which is which before your users do.

```
    ┌─────────────────────────────────────────────────────┐
    │                                                     │
    │   prompt  ───→  LLM  ───→  output  ───→  ???       │
    │                                                     │
    │                            ↑                        │
    │                       is this good?                 │
    │                       is this bad?                  │
    │                       is this the same as yesterday?│
    │                                                     │
    └─────────────────────────────────────────────────────┘
```

Enterprise teams have dedicated ML engineers running elaborate eval suites. You have a git repo and limited patience.

## What solo founders actually need

After trying most of the options, here's what matters:

1. **Works locally** — No mandatory cloud, no signup to try it
2. **Fast feedback** — Minutes, not hours
3. **CI integration** — Catch regressions before merge
4. **Low config** — YAML or simple code, not a platform to learn
5. **Free or cheap** — You're pre-revenue, act like it

## The landscape in 2025

```
                    managed ──────────────────────── open source
                        │                                 │
                        │                                 │
    ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐
    │ LangSmith │  │ Braintrust│  │  Langfuse │  │ Promptfoo │
    └───────────┘  └───────────┘  └───────────┘  └───────────┘
         │              │              │              │
         │              │              │              │
    LangChain      dashboard      self-host         CLI
    ecosystem       heavy          option          first
```

### Promptfoo — The one I actually use

Open source, CLI-first, no cloud required. You define tests in YAML:

```yaml
prompts:
  - "Summarize this: {{text}}"
providers:
  - openai:gpt-4o
  - anthropic:claude-3-5-sonnet
tests:
  - vars:
      text: "Long article here..."
    assert:
      - type: contains
        value: "key point"
      - type: llm-rubric
        value: "Summary captures main argument"
```

Run `promptfoo eval`, get a table. Compare models, compare prompts, catch regressions. Done.

```
    ╭──────────────────────────────────────────────────────╮
    │  $ promptfoo eval                                    │
    │                                                      │
    │  ┌────────┬─────────┬─────────┬────────┐            │
    │  │ Test   │ GPT-4o  │ Claude  │ Llama  │            │
    │  ├────────┼─────────┼─────────┼────────┤            │
    │  │ #1     │   ✓     │   ✓     │   ✗    │            │
    │  │ #2     │   ✓     │   ✓     │   ✓    │            │
    │  │ #3     │   ✗     │   ✓     │   ✗    │            │
    │  └────────┴─────────┴─────────┴────────┘            │
    │                                                      │
    │  Pass rate: 78%                                      │
    ╰──────────────────────────────────────────────────────╯
```

**Why it works for solo:**
- Zero infrastructure
- GitHub Action for CI (catches prompt regressions in PRs)
- Built-in red teaming for security testing
- Works with any provider

### DeepEval — When you need more structure

Pytest-style assertions for LLMs. If you think in unit tests, this clicks immediately.

```python
from deepeval import evaluate
from deepeval.test_case import LLMTestCase
from deepeval.metrics import AnswerRelevancyMetric

test_case = LLMTestCase(
    input="What's our refund policy?",
    actual_output=llm_response,
    expected_output="30 day refund, no questions"
)

evaluate([test_case], [AnswerRelevancyMetric()])
```

60+ built-in metrics. Faithfulness, hallucination, toxicity, RAG-specific stuff.

**Why it works for solo:**
- Familiar testing patterns
- Good for RAG pipelines
- Free core, optional cloud for dashboards

### Langfuse — When you need observability too

More than evals—it's tracing, prompt management, and monitoring in one.

```
    ┌─────────────────────────────────────────────────────┐
    │                    Langfuse                         │
    │                                                     │
    │   traces ────┬──── evals                           │
    │              │                                      │
    │   prompts ───┼──── metrics                         │
    │              │                                      │
    │   logs ──────┴──── dashboards                      │
    │                                                     │
    └─────────────────────────────────────────────────────┘
```

Self-hostable (MIT license), or free cloud tier with 90-day retention.

**Why it works for solo:**
- See what's happening in production
- Debug failed chains step-by-step
- Human annotation for edge cases

### LangSmith — If you're already in LangChain

Deep integration with LangChain/LangGraph. If you're building agents with their framework, the tracing is excellent.

**The catch:** Python-first, tightly coupled to their ecosystem. If you're not using LangChain, skip it.

### Braintrust — If you have a team (you don't)

Great dashboards, collaborative features, non-technical stakeholders can review outputs.

You're a solo founder. You don't need stakeholder alignment. You need to ship.

## My recommendation

```
    start here
        │
        ▼
    ╭─────────╮     yes     ╭───────────╮
    │ Need    │────────────→│ Langfuse  │
    │ tracing?│             ╰───────────╯
    ╰────┬────╯
         │ no
         ▼
    ╭─────────╮     yes     ╭───────────╮
    │ Python  │────────────→│ DeepEval  │
    │ pytest? │             ╰───────────╯
    ╰────┬────╯
         │ no
         ▼
    ╭───────────╮
    │ Promptfoo │  ← start here, actually
    ╰───────────╯
```

**For most solo founders: start with Promptfoo.**

It's the fastest path from "I have prompts" to "I have tested prompts." No signup, no setup, no lock-in. If you outgrow it, you'll know.

Add Langfuse later when you need production observability. The two complement each other—Promptfoo for dev/CI, Langfuse for prod monitoring.

## What I actually do

```
    development              CI                    production
         │                    │                         │
         ▼                    ▼                         ▼
    ┌─────────┐         ┌─────────┐              ┌───────────┐
    │promptfoo│   ───→  │promptfoo│    ───→      │  langfuse │
    │  local  │         │ action  │              │  tracing  │
    └─────────┘         └─────────┘              └───────────┘
         │                    │                         │
    quick iteration     gate merges              debug issues
```

1. **Local:** `promptfoo eval` while developing
2. **CI:** GitHub Action blocks PRs that regress
3. **Prod:** Langfuse traces to debug weird outputs

Total cost: $0 until meaningful scale.

## The unsexy truth

Evals are annoying. Writing test cases for probabilistic systems feels wrong. The output is "correct enough" until it isn't.

But the alternative is finding out from users that your AI is hallucinating. Or worse, not finding out at all.

Start simple. A few assertions in CI beats no assertions in production.

---

*Building with LLMs and figuring it out as you go? Same. Find me on [Twitter/X](https://x.com/laterallyai).*
