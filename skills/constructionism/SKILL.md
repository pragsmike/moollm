---
name: constructionism
description: Educational philosophy — learn by building inspectable things
allowed-tools: []
tier: 0
protocol: CONSTRUCTIONISM
tags: [philosophy, education, papert, drescher, microworld, schema-mechanism]
origin: "Seymour Papert — Logo, Mindstorms"
lineage:
  - "Seymour Papert — Constructionism, Logo, Mindstorms (1980)"
  - "Gary Drescher — Schema Mechanism, Made-Up Minds (1991)"
  - "Marvin Minsky — Society of Mind, K-lines (1986)"
  - "Henry Minsky — pyleela.brain Python implementation"
related: [play-learn-lift, room, yaml-jazz, sister-script, adventure, procedural-rhetoric, schema-mechanism]
---

# Constructionism

> *"If you can build it, you can understand it. If you can inspect it, you can trust it."*

Seymour Papert's educational philosophy: you learn best by **building things** you can **inspect and modify**. Not passive consumption. Not abstract explanation. **Construction.**

## The Tradition

**Logo Microworlds** — Children don't learn geometry from textbooks. They teach a turtle to draw shapes:

```logo
TO SQUARE :SIZE
  REPEAT 4 [FORWARD :SIZE RIGHT 90]
END
```

The child:
1. **Builds** the procedure
2. **Runs** it and sees results
3. **Debugs** when it's wrong
4. **Understands** geometry through construction

## MOOLLM as Microworld

| Logo | MOOLLM |
|------|--------|
| Turtle | Agent/Character |
| Canvas | Room floor |
| Procedures | Skills |
| Variables | YAML state |
| Drawing | File creation |

**Everything is inspectable.** Open `ROOM.yml` — see the state. Read `session-log.md` — see the history. Modify `character.yml` — change the world.

## Core Principles

### Low Floor
Easy to start — no setup, just explore:
```
> LOOK
You are in the workshop.
> EXAMINE hammer
A simple claw hammer.
```

### High Ceiling
Unlimited complexity — build custom skills, complex pipelines, new protocols.

### Wide Walls
Many paths to many goals — adventure games, workflow automation, knowledge organization.

## Learning by Doing

### The Debug Cycle

1. **Try** something — it doesn't work
2. **Inspect** state — see what happened
3. **Hypothesize** — "maybe the path is wrong"
4. **Modify** and retry — test the hypothesis
5. **Understand** — now you know how it works

### Cheating is Learning

From Don's Logo Adventure:

> Type `PRINT :ITEMS` to see where everything is.
> Type `MAKE "RNUM 5` to teleport to the treasure room.
> **If you cheat, you win by learning Logo.**

"Cheating" in MOOLLM:
```
> Open character.yml directly
> Add "magic_sword" to inventory
> You've learned YAML and file structure!
```

The system rewards curiosity with knowledge.

## Micropolis: The Dream

Don's Micropolis for OLPC applied the same philosophy to SimCity:
- Open source simulation
- Scriptable in Python
- Kids can modify the rules
- The city IS the curriculum

MOOLLM applies this to LLM agents:
- Open file state
- Scriptable in any language
- Users can modify the rules
- **The filesystem IS the microworld**

### Embed Micropolis in MOOLLM

```
cities/downtown/
├── ROOM.yml           # Room metadata
├── city.save          # Micropolis save file
├── state.yml          # Extracted game state
├── newspaper/         # Generated stories
├── advisors/          # Expert cards
└── session-log.md
```

LLM reads state, plays the game, summons advisors.

## PLAY-LEARN-LIFT

Constructionism in action:

1. **PLAY** — Explore manually, make messes
2. **LEARN** — Notice patterns, understand
3. **LIFT** — Extract principles, create skills

You don't design skills in the abstract. You **build them** from experience.

---

## Drescher's Schema Mechanism

Gary Drescher's *Made-Up Minds* (1991) extends constructionism into a computational theory of how minds learn causal models of the world. Drescher was a student of Minsky at MIT, and his schema mechanism provides the theoretical foundation for how agents learn from experience.

### The Core Insight

> *"An agent learns by discovering reliable patterns: when I do X in context C, result R tends to follow."*

A **schema** is a causal unit:

```
Context → Action → Result
```

The agent doesn't start with schemas. It **discovers** them through experience, noticing which actions reliably produce which results in which contexts.

### Schema Components

| Drescher | Description | MOOLLM Equivalent |
|----------|-------------|-------------------|
| **Item** | Atomic state element (ON/OFF/UNKNOWN) | YAML field, file existence |
| **Action** | Something the agent can do | Skill verb, procedure |
| **Schema** | Context → Action → Result | Documented procedure |
| **Extended Context** | Statistical tracking of context conditions | "Prerequisites" section |
| **Extended Results** | Statistical tracking of result conditions | "Side Effects" section |
| **Synthetic Item** | Discovered hidden state | Undocumented dependency |
| **Composite Action** | Chained sequence of actions | Multi-step procedure |

### Extended Context: When Does This Work?

A schema might fail unpredictably. Extended Context tracks **which conditions correlate with success**:

```yaml
# The schema "start pyvision" sometimes fails
# Extended Context discovers: it fails when postgres isn't running

schema:
  action: start-pyvision
  context: []  # Initially empty
  result: [pyvision-running]
  
extended_context:
  postgres-running:
    success_when_on: 47    # Succeeded 47 times when postgres was on
    success_when_off: 0    # Never succeeded when postgres was off
    failure_when_on: 2     # Failed 2 times even with postgres
    failure_when_off: 15   # Failed 15 times without postgres
    
# Discovery: postgres-running is a prerequisite!
# Spin off new schema with explicit context:
schema:
  action: start-pyvision
  context: [postgres-running]  # Now explicit
  result: [pyvision-running]
```

This is **marginal attribution** -- discovering which items matter by tracking correlations.

### Extended Results: What Else Happens?

Similarly, schemas track side effects:

```yaml
schema:
  action: ingest-video
  context: [video-exists]
  result: [task-created]
  
extended_results:
  disk-space-decreased:
    on_after_success: 47
    off_after_success: 0
    # Discovery: ingesting uses disk space!
```

### Synthetic Items: Hidden State

Sometimes success depends on state the agent can't directly observe. Drescher's solution: **invent a synthetic item** as a hypothesis.

```yaml
# The schema works sometimes, fails sometimes, no visible pattern
# Hypothesis: there's hidden state we can't see

synthetic_item:
  name: "gpu-memory-available"
  host_schema: start-pyvision
  # If this schema succeeds, assume the item was ON
  # If it fails, assume the item was OFF
```

The synthetic item becomes a **probe** -- its state is inferred from schema success/failure.

### Composite Actions: Planning Through Schemas

Once the agent has reliable schemas, it can chain them:

```yaml
# Goal: pyvision-running
# Current: postgres-not-running

plan:
  - schema: start-postgres
    context: []
    result: [postgres-running]
  - schema: start-pyvision
    context: [postgres-running]
    result: [pyvision-running]
```

Drescher uses **Dijkstra's algorithm** on the schema graph -- find shortest path from current state to goal state.

### The Learning Loop

```
┌─────────────────────────────────────────────────────┐
│  1. ACT                                             │
│     Execute schema action                           │
└─────────────────────────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────┐
│  2. OBSERVE                                         │
│     Record which items changed (on-flips, off-flips)│
└─────────────────────────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────┐
│  3. ATTRIBUTE                                       │
│     Update extended context/results tables          │
│     Track which items correlate with success        │
└─────────────────────────────────────────────────────┘
                         ↓
┌─────────────────────────────────────────────────────┐
│  4. SPIN OFF                                        │
│     When patterns emerge, create child schemas      │
│     with refined context/result conditions          │
└─────────────────────────────────────────────────────┘
```

This is PLAY-LEARN-LIFT at the computational level.

### Implementation: pyleela.brain

Henry Minsky (Marvin's son) implemented Drescher's schema mechanism in Python. The implementation includes:

| Class | Purpose |
|-------|---------|
| `World` | Central coordinator, tracks all items and schemas |
| `Item` | Atomic state element with ON/OFF/UNKNOWN values |
| `Action` | Primitive or composite action |
| `Schema` | The Context → Action → Result unit |
| `ExtendedContext` | Statistical tracking for context discovery |
| `ExtendedResults` | Statistical tracking for result discovery |
| `DijkstraPlanner` | Goal-directed planning through schema graph |

### Connection to MOOLLM Skills

MOOLLM skills are schema systems:

| Drescher | MOOLLM Skill |
|----------|--------------|
| World state | YAML files in skill directory |
| Items | Fields in state files |
| Actions | Skill verbs and procedures |
| Schemas | Documented procedures with context/result |
| Extended Context | Prerequisites, dependencies |
| Extended Results | Side effects, outputs |
| Synthetic Items | Undocumented state the skill discovers |
| Composite Actions | Multi-step procedures |
| Spin-offs | Refined procedures from experience |

**The PLAY-LEARN-LIFT cycle IS schema learning:**
- **PLAY** = Execute actions, observe results
- **LEARN** = Marginal attribution, discover patterns
- **LIFT** = Spin off refined schemas as documented skills

### Neuro-Symbolic Synthesis

Drescher's mechanism is **symbolic** -- explicit rules, logical inference. LLMs are **neural** -- pattern matching, language understanding.

MOOLLM combines both:

| Layer | Nature | Role |
|-------|--------|------|
| **YAML state** | Symbolic | Items, schemas, world state |
| **LLM** | Neural | Pattern recognition, language, creativity |
| **Skills** | Hybrid | Structured knowledge LLM can execute |

The LLM reads schemas empathically. It understands *why* the context matters, not just *that* it matters. This is what Drescher couldn't achieve with 1991 computing -- but LLMs can.

---

## The Insight

> *"If you can build it, you can understand it."*
> *"If you can inspect it, you can trust it."*
> *"The filesystem IS the microworld."*

Drescher adds:

> *"If you can observe patterns, you can discover causality."*
> *"If you track correlations, you can spin off knowledge."*
