# 🎭 MG — Multi-Character Interaction Scenarios

> *"Simulating debates, dialogues, and interactions among characters"*

This directory contains scenarios that simulate interactions and debates among a set of characters. Unlike spatial adventures, these scenarios focus on **dialogue, debate, and character interaction** captured as transcripts.

---

## Structure

```
mg/
├── README.md              # This file
├── SCENARIOS.yml          # Master index of all scenarios (optional)
├── SCENARIO.yml           # Template/legacy (use scenarios/.template-SCENARIO.yml for new scenarios)
├── CHARACTER-RUBRIC.md    # How to score characters for debate effectiveness
├── CHARACTER-SCORES.md    # Current character scores (for reference)
├── BEHAVIORS.md           # Guide to MOOLLM behaviors for scenarios
├── .gitignore             # Excludes private alias files
├── .company-aliases.yml   # PRIVATE: Company name mappings (not for public distribution)
├── .person-aliases.yml    # PRIVATE: Person name mappings (not for public distribution)
├── bios/                  # Source character sketches (to be transformed)
│   └── [character-name].md
├── characters/            # MOOLLM-formatted character files (SHARED across scenarios)
│   ├── README.md          # Character format guide (includes propensities)
│   └── [character-name].yml  # All include debate propensities
├── transcripts/           # Shared transcripts (or use scenario-specific)
│   └── [scenario-name].md
└── scenarios/             # Individual scenario directories
    ├── README.md          # How to create scenarios
    ├── .template-SCENARIO.yml  # Template to copy for new scenarios
    └── [scenario-name]/   # e.g., "echopoint-consultation", "monica-meeting"
        ├── README.md      # Scenario description, setup, narrative context
        ├── SCENARIO.yml   # Scenario-specific state (participants, topic, etc.)
        └── transcripts/   # Scenario-specific transcripts (optional)
            └── [session].md
```

---

## Multiple Scenarios

### Scenario Types

**Linear Narrative (Sequential Scenes):**
```
scenarios/
├── act-1-consultation/      # Scene 1: Echopoint team meets consultants
├── act-2-debate/             # Scene 2: Technical debate
└── act-3-resolution/         # Scene 3: Final decision
```

**Alternate Realities (Parallel Timelines):**
```
scenarios/
├── timeline-a-standard/      # Reality A: Standard consultation
├── timeline-b-aggressive/    # Reality B: Aggressive timeline
└── timeline-c-budget-cut/   # Reality C: Budget constraints
```

**Mixed Structure:**
```
scenarios/
├── echopoint-consultation/   # Echopoint team + Marcus's committee
├── monica-meeting/           # Monica + post-production team
├── elodie-interview/         # Elodie solo interview
└── cross-scenario-debate/    # Characters from multiple scenarios
```

### Character Subsets

Each scenario uses a **subset** of characters from `characters/`. Characters are shared across scenarios, but each scenario tracks:
- Which characters are active participants
- Their relationships and dynamics in this specific context
- Scenario-specific goals and positions

---

## Workflow

1. **Add bios** → Place character sketches in `bios/` (markdown format)
2. **Transform** → Convert bios to MOOLLM character files in `characters/`
   - **Important:** Ensure characters include **debate propensities** (see `characters/README.md`)
   - Use `CHARACTER-RUBRIC.md` to evaluate character quality for debates
3. **Create scenario directory** → `scenarios/[scenario-name]/`
4. **Set up SCENARIO.yml** → Copy from `scenarios/.template-SCENARIO.yml` and define:
   - Active participants (character file paths)
   - Topic and type (debate, roundtable, etc.)
   - Protocol/behavior (e.g., `DEBATE`, `ADVERSARIAL-COMMITTEE`, `ROBERTS-RULES`)
5. **Run interaction** → LLM simulates dialogue/debate using character files
6. **Capture transcript** → Save to scenario's `transcripts/` or shared `transcripts/`

---

## Key Differences from Adventures

| Adventure | MG Scenario |
|-----------|-------------|
| Spatial exploration | Dialogue/interaction |
| `ADVENTURE.yml` | `SCENARIO.yml` |
| Rooms (directories) | Topics/rounds |
| Objects to collect | Arguments/positions |
| Navigation commands | Dialogue prompts |
| Inventory | Beliefs/positions |

---

## Character Format

Characters are MOOLLM-formatted YAML files with:
- **Personality traits** (Sims-style or Mind Mirror)
- **Background/biography**
- **Debate propensities** (type, risk tolerance, epistemology) — **REQUIRED for effective debates**
- **Beliefs/positions** on topics
- **Speaking style** and vocabulary
- **Relationships** with other characters
- **Goals** in the scenario

**Critical:** All characters include **explicit propensities** that define their debate role and perspective. This is essential for structured, productive debates. See `characters/README.md` for details on propensities.

See `characters/` for examples after transformation.

---

## Scenario Types

- **Debates** — Structured arguments on specific topics
- **Roundtables** — Open discussion among multiple characters
- **Interviews** — One-on-one or panel interviews
- **Symposia** — Academic-style presentations and Q&A
- **Dialogues** — Two-person conversations
- **Consultations** — Expert advice sessions
- **Meetings** — Business/professional discussions

---

## Usage

1. **Add character bios** → Place sketches in `bios/` (markdown format)
2. **Transform characters** → "Transform the bios in mg/bios/ into MOOLLM character files"
   - Characters will include debate propensities automatically
   - Review `CHARACTER-SCORES.md` to see how characters score
3. **Evaluate characters** → Use `CHARACTER-RUBRIC.md` to assess debate readiness
4. **Create scenario** → Create directory in `scenarios/` and copy `.template-SCENARIO.yml`
5. **Configure scenario** → Set active participants, topic, protocol (e.g., `DEBATE`, `ADVERSARIAL-COMMITTEE`)
6. **Run interaction** → "Start the scenario — have them discuss [topic] for 5 rounds"
7. **Review transcripts** → Saved automatically to scenario's `transcripts/` or shared `transcripts/`

**See `BEHAVIORS.md`** for available MOOLLM behaviors you can use in scenarios.

---

## Scenario Relationships

For linear narratives or connected scenarios, document relationships in:
- Each scenario's `README.md` (links to previous/next)
- `SCENARIOS.yml` (master index with relationships)

Example:
```yaml
# SCENARIOS.yml
scenarios:
  echopoint-consultation:
    type: consultation
    participants: [echopoint-team, marcus-committee]
    follows: null
    precedes: echopoint-decision
    
  echopoint-decision:
    type: debate
    participants: [echopoint-team]
    follows: echopoint-consultation
    precedes: null
```

---

## Key Concepts

### Debate Propensities

All characters include **explicit propensities** that define their debate role:
- **Type** (e.g., `operational_realism`, `paranoid_realism`, `idealism`)
- **Risk tolerance** (low, medium, high, varies)
- **Epistemology** (how they determine truth)
- **What they surface** (blind spots they reveal)
- **Distinctive voice** (signature phrase)

Propensities ensure characters challenge from different angles, preventing premature consensus and forcing comprehensive exploration. See `characters/README.md` for details.

### Character Evaluation

Use `CHARACTER-RUBRIC.md` to score characters (0-100 points) on debate effectiveness. `CHARACTER-SCORES.md` shows current character scores for reference.

### MOOLLM Behaviors

See `BEHAVIORS.md` for predefined behaviors you can use:
- **DEBATE** — Structured multi-perspective deliberation
- **ADVERSARIAL-COMMITTEE** — Committee with opposing views
- **ROBERTS-RULES** — Parliamentary procedure
- **SOUL-CHAT** — Free-form character conversations
- **SPEED-OF-LIGHT** — Simulate many turns in one call

Invoke by mentioning the protocol name (e.g., `DEBATE`) or structuring your scenario accordingly.

### Committee Selection

Use the `FORM-SMART` method from `skills/adversarial-committee/` to automatically select diverse committee members from your character pool. See `COMMITTEE-SELECTION.md` for local guidance, or `skills/adversarial-committee/SELECTION.md` for the full selection guide.

**Strategies:** `core`, `balanced`, `consensus`, `evidence`, `innovation`

### Company/Person Aliases

Character bios use fictional aliases for real companies and people to avoid legal issues. The alias mappings are in private files (`.company-aliases.yml`, `.person-aliases.yml`) excluded from git.

---

*See [bios/README.md](bios/README.md) for bio format guidelines.*  
*See [characters/README.md](characters/README.md) for character format and propensities.*  
*See [scenarios/README.md](scenarios/README.md) for how to create scenarios.*
