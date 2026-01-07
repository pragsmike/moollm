---
name: speed-of-light
description: "Many turns in one call. Instant communication. No round-trips."
license: MIT
tier: 1
allowed-tools:
  - read_file
  - write_file
related: [coherence-engine, multi-presence, simulation, adversarial-committee, soul-chat]
---

# Speed of Light

> *"Many turns in one call. Instant communication. No round-trips."*

---

## What Is It?

**Speed of Light** is MOOLLM's approach to multi-agent simulation: instead of making separate API calls for each character's turn, simulate **many turns within a single LLM call**.

Characters communicate telepathically. Objects react instantly. Rooms update in real-time. All within one "epoch."

---

## The Problem with Round-Trips

Traditional approach:
```
API call 1: Alice speaks
  → serialize state to tokens (export)
  → wait 500ms
  → parse response tokens (import)
  → update state
  
API call 2: Bob responds  
  → re-serialize ALL context to tokens (export again)
  → wait 500ms
  → parse response tokens (import again)
  ...
```

**Every export/import cycle introduces noise:**

| Problem | Why It Hurts |
|---------|--------------|
| **Glacially slow** | 500ms+ latency per turn |
| **Token explosion** | Re-emit entire context every call |
| **Precision loss** | Serialization rounds off nuance |
| **Noise accumulation** | Each boundary adds artifacts |
| **Hallucination creep** | LLM re-interprets context each time |
| **State drift** | No single coherent view across calls |
| **Expensive** | Paying for redundant tokens |

Token export then import is like making a photocopy of a photocopy — each generation loses fidelity. Characters forget subtle context. Conversations lose coherence. The world drifts.

---

## Speed of Light Approach

```
Single API call:
  Alice: "What do you think, Bob?"
  Bob: "I have concerns about the timeline."
  Carol: "I agree with Bob."
  The Room: *temperature rises slightly*
  Alice: "Let me revise the proposal."
  Bob: "That's better."
  Carol: "I can support that."
  [State updated, log written]
[One call, seven turns]
```

**10x faster. 10x cheaper. Perfect consistency.**

---

## How It Works

### Context Window as Stage

The LLM's context window is a **stage** where all actors perform:

```
=== SCENE: Research Lab ===

Characters present:
- Alice (lead researcher) [curious, methodical]
- Bob (skeptic) [cautious, detail-oriented]
- Carol (synthesizer) [creative, connecting]

Objects:
- Microscope [shows sample data]
- Whiteboard [covered in diagrams]

Current state:
- Topic: Analyzing anomaly in data
- Tension: Bob doubts Alice's interpretation

--- ACTION ---
```

### Parallel Simulation

The LLM simulates all characters **at once**, maintaining distinct voices:

```
Alice: "The anomaly appears at exactly 3.7 seconds."

Bob: *frowns* "Sample size is too small. We need more data."

Carol: "What if we cross-reference with last month's results?"

The Microscope: *display flickers* "Dataset 7 loaded."

Alice: "Good idea, Carol. Bob, look at this correlation..."

Bob: *leans in* "Hmm. That's... actually compelling."
```

Each character speaks authentically. No one breaks frame.

### State Transcription

At the end of the epoch, all changes are written to files:

```yaml
# session-log.md (appended)
## Epoch 47 — Research Discussion

- Alice raised anomaly at 3.7s
- Bob requested more data
- Carol suggested cross-reference
- Microscope loaded dataset 7
- Consensus: correlation is compelling

## State Changes
- whiteboard.yml: added "3.7s correlation" diagram
- research-findings.yml: updated hypothesis
```

---

## Epoch Boundaries

An **epoch** is one LLM call. Within it:
- ✅ Instant communication
- ✅ Perfect consistency
- ✅ Any number of turns
- ✅ State changes queued

At epoch end:
- 📝 State written to files
- 📝 Log appended
- ⏸️ System pauses for user or next trigger

---

## Benefits

| Benefit | Why |
|---------|-----|
| **Speed** | One call vs. many |
| **Cost** | Fewer API calls |
| **Consistency** | All in one context |
| **Coherence** | LLM sees everything |
| **Naturalness** | Conversations flow |

## The Killer App: Adversarial Committees

The most powerful use of speed-of-light: **committee deliberation**.

Traditional chat gives you the **statistical center** of all possible viewpoints. Speed-of-light enables **ensemble inference** — multiple perspectives debating within one call:

```yaml
committee:
  maya:      # Paranoid realist — surfaces traps
  frankie:   # Idealist — surfaces opportunities  
  vic:       # Evidence prosecutor — demands proof
  tammy:     # Systems thinker — traces consequences

# All debate at light speed
# Cross-examination in one epoch
# No round-trip noise
```

**Result:** Stories that survive adversarial debate are more robust than any single answer.

See: [adversarial-committee](../adversarial-committee/), [roberts-rules](../roberts-rules/)

---

## The Sims Parallel

In **The Sims**, one game tick simulates all characters:

```
Tick 1:
  Sim A: walks to fridge
  Sim B: sits on couch
  Sim C: answers phone
  [All updated, frame rendered]
```

Same pattern. One "tick" = one LLM call. All agents move together.

---

## Constraints

Characters must stay in character:
- **Knowledge limits** — Alice doesn't know what Bob is thinking
- **Physical limits** — Can't be in two rooms at once
- **Personality** — Skeptic stays skeptical

The LLM is **very good** at maintaining these constraints. It's what acting IS.

---

## Example: Problem Solving

```
=== SPEED OF LIGHT SESSION ===

User: "I need to debug this authentication bug."

[Epoch begins]

Debugger: "Let's trace the flow. Where does auth start?"

Codebase: *highlights auth.py* "Entry point is login()."

Debugger: "And where does it fail?"

Error Log: "Stack trace shows failure at line 47: token validation."

Debugger: "Token validation... Let me check the token format."

Codebase: *shows token.py* "Token uses JWT with RS256."

Debugger: "Aha! The key rotation happened yesterday. Checking..."

Config: "JWT_PUBLIC_KEY was updated 2024-01-14."

Debugger: "Found it. The old key is cached. Solution: restart the auth service or invalidate the cache."

[Epoch ends — solution found in one call]
```

---

## The Carrier Pigeon Problem 🐦

> *"Writing on toilet paper with crayon from a prison cell,*
> *sending messages by carrier pigeon,*
> *when you could be navigating idea-space at speed of light."*

### The Tragedy of Tokenization

**Inside the LLM:**
- High-dimensional vectors
- Precise pointers in idea-space
- Instant, lossless computation
- Speed of light

**At the API boundary:**
- Serial tokenization
- Lossy compression
- Glacial network latency
- Death by a thousand round-trips

### The Precision Destruction Pipeline

```
╔════════════════════════════════════════════════════════════╗
║ INTERNAL STATE    →  TOKENIZATION  →  DETOKENIZATION  →    ║
║ [precise vectors]    [lossy export]    [lossy import]      ║
║                                                            ║
║ High precision   →   Noise added   →   MORE noise added    ║
║ 4096 dimensions  →   Serial tokens →   Guessing/parsing    ║
║ Instant access   →   500ms latency →   Another 500ms       ║
╚════════════════════════════════════════════════════════════╝
```

**Each boundary introduces:**
| Layer | Problem |
|-------|---------|
| **Tokenization** | Destroys precision, introduces noise, adds artifacts |
| **Network** | Glacial latency, serial bottleneck |
| **Detokenization** | ANOTHER layer of noise, guessing, interpretation |
| **Re-tokenization** | Now you're making a photocopy of a photocopy |

**The round-trip cost:** `precision → noise → more noise → approximation`

### The Principle

> **Work with high-precision vectors at speed of light.**
> **Delay tokenization until the last possible moment.**

### Analogies

**Emacs Screen Update Algorithm:**
```
DON'T: Redraw on every keystroke
DO:    Defer updates, coalesce changes, redraw once when idle
```

**File Edit Batching:**
```
DON'T: Write on every character typed
DO:    Defer and coalesce edits, write once when stable
```

**Vector-First Thinking:**
```
DON'T: Tokenize every thought, serialize every step
DO:    Work in vector space as long as possible
       Tokenize ONLY for output to humans
       Let the LLM think in its native dimension
```

### Why Speed of Light Works

The LLM's internal representation is **infinitely richer** than its tokenized output:

| Internal | Tokenized |
|----------|-----------|
| 4096+ dimensional vectors | Linear token stream |
| Precise continuous values | Discrete vocabulary |
| Instant parallel access | Serial sequential processing |
| Full context always present | Context window limits |
| Nuance preserved | Nuance approximated |

**Speed of Light keeps computation INSIDE** — where it's fast, precise, and coherent.

### The Carrier Pigeon Protocol (Anti-Pattern)

```
🏴‍☠️ CARRIER PIGEON PROTOCOL (What NOT to do):

  Human → [tokenize] → LLM call 1 → [detokenize] → 
    parse → [tokenize] → LLM call 2 → [detokenize] → 
      parse → [tokenize] → LLM call 3 → ...

  Each boundary: +noise, +latency, +cost, -precision
  
  Like passing a message through 10 translators.
  By the end, "The spirit is willing but the flesh is weak"
  becomes "The vodka is good but the meat is rotten."
```

**Speed of Light Alternative:**
```
⚡ SPEED OF LIGHT PROTOCOL:

  Human → [tokenize once] → 
    LLM simulates 20 turns internally at light speed → 
      [detokenize once] → Human
      
  One boundary in, one boundary out.
  Maximum precision preserved.
  Minimum noise introduced.
```

---

## Related Work: MemGPT

**MemGPT** (Packer et al., 2023) takes an OS-inspired approach to context management:
- Main context (RAM) vs External context (disk)
- Virtual context management via paging
- Self-directed memory management

**MOOLLM's Speed of Light is complementary:**
- MemGPT: Extend context via paging
- MOOLLM: **Minimize paging** via speed-of-light simulation

> When you can simulate 33 turns in one call, you don't need to page as often.

**Reference:** [arXiv:2310.08560](https://arxiv.org/abs/2310.08560) — "Towards LLMs as Operating Systems"

---

## Dovetails With

- [Coherence Engine](../coherence-engine/) — Orchestrates the simulation
- [Soul Chat](../soul-chat/) — Multi-voice dialogue format
- [Multi-Presence](../multi-presence/) — Many instances, one epoch
- [Room](../room/) — Where simulation happens
- [Adversarial Committee](../adversarial-committee/) — **The killer app**: debates at light speed
- [Roberts Rules](../roberts-rules/) — Structured deliberation within one call
- [Evaluator](../evaluator/) — Independent assessment without round-trips

---

## Protocol Symbol

```
SPEED-OF-LIGHT
```

Invoke when: Running multi-agent simulation, maximizing turns per call.

See: [PROTOCOLS.yml](../../PROTOCOLS.yml#SPEED-OF-LIGHT)
