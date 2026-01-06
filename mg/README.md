# 🎭 MG — Multi-Character Interaction Scenarios

> *"Simulating debates, dialogues, and interactions among characters"*

This directory contains scenarios that simulate interactions and debates among a set of characters. Unlike spatial adventures, these scenarios focus on **dialogue, debate, and character interaction** captured as transcripts.

---

## Structure

```
mg/
├── README.md              # This file
├── SCENARIOS.yml          # Master index of all scenarios (optional)
├── bios/                  # Source character sketches (to be transformed)
│   └── [character-name].md
├── characters/            # MOOLLM-formatted character files (SHARED across scenarios)
│   └── [character-name].yml
├── transcripts/           # Shared transcripts (or use scenario-specific)
│   └── [scenario-name].md
└── scenarios/             # Individual scenario directories
    ├── [scenario-name]/   # e.g., "echopoint-consultation", "monica-meeting", "timeline-a"
    │   ├── README.md      # Scenario description, setup, narrative context
    │   ├── SCENARIO.yml   # Scenario-specific state (participants, topic, etc.)
    │   └── transcripts/   # Scenario-specific transcripts (optional)
    │       └── [session].md
    └── ...
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
3. **Create scenario directory** → `scenarios/[scenario-name]/`
4. **Set up SCENARIO.yml** → Define active participants, topic, type
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
- **Beliefs/positions** on topics
- **Speaking style** and vocabulary
- **Relationships** with other characters
- **Goals** in the scenario

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

1. Add your character bios to `bios/`
2. Transform: "Transform the bios in mg/bios/ into MOOLLM character files"
3. Create scenario: "Create a scenario directory 'echopoint-consultation' with Echopoint team + Marcus's committee"
4. Run: "Start the scenario — have them discuss the facility upgrade for 5 rounds"
5. Review: Transcripts are saved automatically

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

*See [bios/README.md](bios/README.md) for bio format guidelines.*
*See [scenarios/](scenarios/) for individual scenario directories.*
