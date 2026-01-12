# 🎭 Adversarial Committee

> "No single story is true — but the ensemble approximates actionable wisdom."

## MOOLLM K-Lines

| K-Line | Why Related |
|--------|-------------|
| [moollm/](../moollm/) | Many-voiced IS MOOLLM |
| [society-of-mind/](../society-of-mind/) | Committee IS a society deliberating |
| [debate/](../debate/) | Structured deliberation |
| [roberts-rules/](../roberts-rules/) | Parliamentary procedure |
| [rubric/](../rubric/) | Scoring criteria |
| [evaluator/](../evaluator/) | Independent assessment |
| [soul-chat/](../soul-chat/) | Multi-agent conversation |
| [persona/](../persona/) | Committee members have personas |
| [speed-of-light/](../speed-of-light/) | All debate in one call |
| [designs/mike-gallaher-ideas.md](../../designs/mike-gallaher-ideas.md) | Mike Gallaher's methodology |

**Quick Links:**
- [Full Specification](SKILL.md) — complete protocol
<<<<<<< HEAD
- [Selection Guide](SELECTION.md) — smart committee selection
- [Background](../../designs/mike-gallaher-ideas.md) — Mike Gallaher's methodology
=======
>>>>>>> upstream/main

## Overview

Create a roster of characters with opposing propensities to force genuine debate. Each persona surfaces different blind spots and challenges different assumptions.

### Formation Options

| Method | Use When |
|--------|----------|
| `FORM` | You know exactly which personas to include |
| `FORM-SMART` | You have a character pool and want smart selection |

**FORM-SMART** analyzes a character pool and selects diverse members based on:
- Propensity type (paranoid, idealist, operational, etc.)
- Risk tolerance (low, medium, high)
- Epistemology (how they determine truth)
- Debate role (devil's advocate, opportunity scout, etc.)

**Strategies:** `core`, `balanced`, `consensus`, `evidence`, `innovation`

## The Committee Pattern

| Character | Propensity | What They Surface |
|-----------|------------|-------------------|
| **Maya** | Paranoid realism | Political dynamics, hidden agendas |
| **Frankie** | Idealism | Value conflicts, missed opportunities |
| **Joe** | Continuity guardian | Institutional memory, precedent |
| **Vic** | Evidence prosecutor | Proof demands, data gaps |
| **Tammy** | Systems thinker | Feedback loops, unintended consequences |

## Why It Works

LLMs give statistically-likely answers that encode:
- Survivorship bias
- Genre conventions  
- Hidden assumptions

Adversarial debate performs **structured perturbation of the narrative space** — stories that survive cross-examination are more robust.

## Credits

**Mike Gallaher** — Core methodology, committee patterns, propensity design.

See: [designs/mike-gallaher-ideas.md](../../designs/mike-gallaher-ideas.md)

<<<<<<< HEAD
## Quick Example

```yaml
# Smart selection from character pool
FORM-SMART name="Strategy Review" pool="characters/" strategy="core" size=5

# Creates committee with:
# - maya-tilted-hat (paranoid_realism, devil's_advocate)
# - frankie-kerouac (idealism, opportunity_scout)
# - joe-gusher (continuity_guardian, historian)
# - vic-eyebrow (evidence_prosecutor, evidence_checker)
# - tammy-silent (systems_thinking, systems_analyst)
```

## Related Skills

- [roberts-rules](../roberts-rules/) — Parliamentary procedure
- [rubric](../rubric/) — Scoring criteria
- [evaluator](../evaluator/) — Independent assessment
- [soul-chat](../soul-chat/) — Multi-agent conversation
- [speed-of-light](../speed-of-light/) — Instant simulation
=======
>>>>>>> upstream/main
