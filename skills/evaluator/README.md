# 🔍 Evaluator

> "The committee can't see what the evaluator is thinking."

**Quick Links:**
- [Full Specification](SKILL.md) — complete protocol
- [Background](../../designs/mike-gallaher-ideas.md) — Mike Gallaher's methodology

## Overview

An **independent evaluator** assesses committee output without access to debate context. This adversarial separation prevents the committee from gaming their own metrics.

## Why Independence?

If the committee sees how they'll be evaluated:
- They optimize for the score, not the outcome
- Arguments become performative
- Genuine disagreement gets smoothed over

Independent evaluation:
- Sees only the output, not the process
- Can't be influenced by committee dynamics
- Applies rubric without bias from debate

## The Pattern

```
Committee Room                    Evaluation Room
     │                                 │
     │ [heated debate]                 │
     │                                 │
     └──── OUTPUT ────────────────────►│
                                       │ [no context]
                                       │ [applies RUBRIC]
                                       │
     ┌──── CRITIQUE ◄─────────────────┘
     │
     │ [if score fails]
     │ [revision loop]
     ▼
```

## Credits

**Mike Gallaher** — Independent evaluator pattern, adversarial loop design.

See: [designs/mike-gallaher-ideas.md](../../designs/mike-gallaher-ideas.md)

## Related Skills

- [adversarial-committee](../adversarial-committee/) — What gets evaluated
- [rubric](../rubric/) — Scoring criteria
- [roberts-rules](../roberts-rules/) — Structured deliberation
- [room](../room/) — Inbox/outbox for throwing output
