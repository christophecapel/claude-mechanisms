# Trace the cascade before exiting plan mode

> For any change that touches a pipeline, trace every downstream consumer before finalizing.

## The mechanism

For any change that touches a pipeline (data flows through multiple stages), explicitly trace every downstream consumer: "If stage N's output changes after stage N+1 has already consumed it, what happens?"

Walk the full chain. Do not finalize the plan until every stage has been traced.

## Why this exists

A plan to fix daily log staleness initially looked complete. But user feedback forced cascade tracing which revealed three additional gaps: weekly summaries consumed stale Friday data, monthly summaries consumed stale last-Friday-of-month data, and ad-hoc corrections needed a backfill path. Each expansion fundamentally changed the design. The initial "complete" plan would have shipped a partial fix.

## How to apply

Add to your `CLAUDE.md`:

```
Trace the cascade before exiting plan mode -- for any change that touches a pipeline, trace every downstream consumer. "If stage N's output changes after stage N+1 has already consumed it, what happens?"
```

Before finalizing any plan that involves data flowing through stages, enumerate every stage and ask the cascade question. The answer is always either a reconciliation mechanism or an explicit "this is acceptable staleness."
