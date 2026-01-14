# 🎭 Predefined Behaviors for Scenarios

MOOLLM includes many predefined behaviors you can use in your scenarios. These are activated through **Protocol Symbols (K-Lines)** or **Skills**.

---

## 🎯 Scenario-Specific Behaviors

### 1. **DEBATE** — Structured Multi-Perspective Deliberation

**Protocol:** `DEBATE`  
**Skill:** `skills/debate/`

Structured adversarial dialogue that forces genuine exploration. Perfect for:
- Technical debates (e.g., facility upgrade decisions)
- Policy discussions
- Philosophical arguments
- Any decision requiring multiple perspectives

**How it works:**
- Multiple sides with advocates
- Moderator enforces turn-taking
- Cross-examination phase
- Evidence phase
- Final positions with confidence scores

**Example:**
```yaml
# In your SCENARIO.yml
scenario:
  type: debate
  protocol: DEBATE
  
  sides:
    - name: "Pro Upgrade"
      advocates: [frankie-kerouac, sofia-ramirez]
    - name: "Con Upgrade"  
      advocates: [maya-tilted-hat, jamal-washington]
```

**Invoke:** Mention `DEBATE` or use the debate skill structure.

---

### 2. **ADVERSARIAL-COMMITTEE** — Committee with Opposing Views

**Protocol:** `ADVERSARIAL-COMMITTEE`  
**Skill:** `skills/adversarial-committee/`

Committee of personas with incompatible values that debate to surface blind spots. Perfect for:
- Decision-making scenarios
- Strategy reviews
- Risk assessment
- Complex evaluations

**How it works:**
- Each member has a different propensity (paranoid, idealist, evidence-focused, etc.)
- They debate through structured rounds
- Forces exploration of decision space
- Prevents premature consensus

**Example:**
```yaml
# Your Echopoint team IS an adversarial committee!
committee:
  members:
    - maya: paranoid_realism
    - frankie: idealism
    - joe: continuity_guardian
    - vic: evidence_prosecutor
    - tammy: systems_thinking
```

**Invoke:** Mention `ADVERSARIAL-COMMITTEE` or structure as committee.

---

### 3. **ROBERTS-RULES** — Parliamentary Procedure

**Protocol:** `ROBERTS-RULES`  
**Skill:** `skills/roberts-rules/`

Parliamentary procedure that prevents LLMs from short-circuiting to likely conclusions. Perfect for:
- Formal meetings
- Structured decision-making
- Professional consultations
- Any scenario needing formal process

**Stages:**
1. Call to order
2. Review minutes
3. New business
4. Motion → Second → Debate → Vote
5. Adjourn

**Example:**
```yaml
# In SCENARIO.yml
scenario:
  type: meeting
  protocol: ROBERTS-RULES
  
  chair: marcus-chen  # Runs the meeting
  agenda:
    - "Facility upgrade proposal"
    - "Budget allocation"
```

**Invoke:** Mention `ROBERTS-RULES` or structure as formal meeting.

---

### 4. **SOUL-CHAT** — Character Dialogues

**Protocol:** `SOUL-CHAT`  
**Skill:** `skills/soul-chat/`

"Everything is alive. Everything can speak." YAML Jazz conversations between characters, objects, rooms, concepts. Perfect for:
- Free-form character interactions
- Multi-perspective exploration
- Character-to-character dialogues
- Objects/rooms/concepts speaking

**Format:** Markdown with embedded YAML blocks

**Example:**
```markdown
## Frankie

I think we should go for it. The opportunity is huge.

```yaml
position: pro
confidence: 0.8
reason: "Growth opportunity"
```

## Maya

But what aren't they telling us? Who benefits if this goes sideways?

```yaml
position: con
confidence: 0.9
concern: "Hidden agenda"
```
```

**Invoke:** Mention `SOUL-CHAT` or use markdown dialogue format.

---

### 5. **SPEED-OF-LIGHT** — Multi-Agent Simulation

**Protocol:** `SPEED-OF-LIGHT`  
**Skill:** `skills/speed-of-light/`

Simulate many turns/agents inside ONE LLM call. Perfect for:
- Multiple characters interacting simultaneously
- Parallel deliberations
- Ensemble conversations
- Fast-paced multi-character scenes

**How it works:**
- All characters speak in one LLM call
- No round trips
- Natural conversation flow
- Characters respond to each other in real-time

**Example:**
```yaml
# In SCENARIO.yml
scenario:
  protocol: SPEED-OF-LIGHT
  
  # All these characters interact in ONE call:
  active_participants:
    - frankie-kerouac
    - maya-tilted-hat
    - marcus-chen
    - sofia-ramirez
```

**Invoke:** Mention `SPEED-OF-LIGHT` or structure as ensemble.

---

### 6. **ACTION-QUEUE** — Task Scheduling

**Protocol:** `ACTION-QUEUE`  
**Skill:** `skills/action-queue/`

Sims-inspired task scheduling. Characters queue actions that execute in order. Perfect for:
- Multi-step character actions
- Complex workflows
- Character planning
- Sequential task execution

**How it works:**
- Characters build action queues
- Objects can push prerequisites
- Actions execute in order
- Can interrupt, reorder, cancel

**Example:**
```yaml
# Character has action queue
character:
  action_queue:
    - action: "EXAMINE proposal"
    - action: "CONSULT marcus"
    - action: "DRAFT response"
    - action: "SEND to committee"
```

**Invoke:** Mention `ACTION-QUEUE` or structure actions as queue.

---

### 7. **ADVERTISEMENT** — Objects Broadcast Actions

**Protocol:** `ADVERTISEMENT`  
**Skill:** `skills/advertisement/`

Objects broadcast available actions with scores. Characters choose from what's advertised. Perfect for:
- Interactive objects
- Contextual actions
- Dynamic interaction options
- Sims-style object behavior

**How it works:**
- Objects advertise what they can do
- Each action has a score
- Characters pick highest-scored actions
- Enables emergent behavior

**Example:**
```yaml
# An object advertises actions
object:
  name: "Proposal Document"
  advertisements:
    READ:
      score: 90
      condition: "character has time"
    ANALYZE:
      score: 70
      condition: "character has expertise"
    CHALLENGE:
      score: 60
      condition: "character is skeptical"
```

**Invoke:** Mention `ADVERTISEMENT` or structure objects with advertisements.

---

## 🔧 Core Protocols (Always Available)

### **POSTEL** — Charitable Interpretation

**Protocol:** `POSTEL`

"Be liberal in what you accept, conservative in what you emit." Makes the LLM interpret ambiguous input charitably.

**Use when:** Characters receive unclear messages, need to interpret intent, handle edge cases.

---

### **YAML-JAZZ** — Semantic Comments

**Protocol:** `YAML-JAZZ`

Comments carry meaning. The LLM reads and interprets comments as data.

**Use when:** Writing character files, scenario files, any YAML that needs semantic interpretation.

---

### **COHERENCE-ENGINE** — Consistency Maintainer

**Protocol:** `COHERENCE-ENGINE`

The LLM maintains consistency across distributed state, orchestrates simulations, referees conflicts.

**Use when:** Multiple characters interacting, maintaining world state, resolving conflicts.

---

### **PLAY-LEARN-LIFT** — Exploration Methodology

**Protocol:** `PLAY-LEARN-LIFT`

Three-stage methodology: explore → find patterns → share as skills.

**Use when:** Characters are learning, exploring new topics, discovering solutions.

---

## 📋 Decision & Evaluation Tools

### **RUBRIC** — Measurable Criteria

**Protocol:** `RUBRIC`  
**Skill:** `skills/rubric/`

Translates qualitative debate to quantitative scores. Defines explicit criteria for evaluation.

**Use when:** Need to compare options, evaluate proposals, make data-driven decisions.

---

### **EVALUATOR** — Independent Assessment

**Protocol:** `INDEPENDENT-EVALUATOR`  
**Skill:** `skills/evaluator/`

Independent assessment without debate context. Prevents gaming the system.

**Use when:** Need unbiased evaluation of committee output, final assessment.

---

## 🎮 Game Mechanics (If Needed)

### **NEEDS** — Dynamic Motivations

**Protocol:** `NEEDS-AS-MOTIVATION`  
**Skill:** `skills/needs/`

Sims-style dynamic needs (hunger, energy, fun, social) that drive behavior.

**Use when:** Characters have fluctuating motivations, needs affect decisions.

---

### **BUFF** — Temporary Effects

**Protocol:** `BUFF-AS-MODIFIER`  
**Skill:** `skills/buff/`

Temporary effects system. Curses are just shitty buffs.

**Use when:** Characters have temporary conditions, effects modify behavior.

---

### **TIME** — Narrative Time Flow

**Protocol:** `TIME-AS-NARRATIVE`  
**Skill:** `skills/time/`

Simulation turns vs LLM iterations. Tracks narrative time.

**Use when:** Need to track time passing, buff durations, turn-based mechanics.

---

## 🎨 How to Use in Your Scenarios

### Option 1: Mention Protocol Names

Just mention the protocol in your scenario description or SCENARIO.yml:

```yaml
scenario:
  name: "Facility Upgrade Debate"
  protocol: [DEBATE, ROBERTS-RULES, SPEED-OF-LIGHT]
  # LLM will use these behaviors
```

### Option 2: Structure as Skill

Follow the skill's structure from `skills/[skill-name]/SKILL.md`:

```yaml
# For debate structure
debate:
  topic: "Should we upgrade the facility?"
  sides:
    - name: "Pro"
      advocates: [frankie, sofia]
    - name: "Con"
      advocates: [maya, jamal]
```

### Option 3: Reference in README

Document which behaviors you're using:

```markdown
# Scenario: Facility Upgrade Debate

**Protocols:** DEBATE, ROBERTS-RULES, SPEED-OF-LIGHT

This scenario uses structured debate with parliamentary procedure...
```

---

## 📚 Full List of Available Skills

See `skills/INDEX.yml` for complete catalog. Key ones for scenarios:

| Skill | Use Case |
|-------|----------|
| `debate` | Structured adversarial dialogue |
| `adversarial-committee` | Multi-perspective decision-making |
| `roberts-rules` | Formal meeting procedure |
| `soul-chat` | Free-form character dialogues |
| `speed-of-light` | Multi-agent simulation |
| `action-queue` | Task scheduling |
| `advertisement` | Object action broadcasting |
| `rubric` | Evaluation criteria |
| `evaluator` | Independent assessment |

---

## 🔍 Finding More

- **Protocols:** See `PROTOCOLS.yml` for all K-Line activators
- **Skills:** See `skills/INDEX.yml` for full skill catalog
- **Examples:** See `examples/adventure-2/` for real usage examples

---

*These behaviors are designed to work together. Mix and match as needed for your scenarios!*

