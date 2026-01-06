# 📋 Scenarios

Individual scenario directories live here.

Each scenario is a self-contained interaction with its own:
- **SCENARIO.yml** — State file (participants, topic, dialogue state)
- **README.md** — Description, setup, narrative context
- **transcripts/** (optional) — Scenario-specific transcripts

## Structure

```
scenarios/
├── README.md              # This file
├── .template-SCENARIO.yml  # Template to copy for new scenarios
└── [scenario-name]/
    ├── README.md          # Scenario description and setup
    ├── SCENARIO.yml       # Scenario state (participants, topic, etc.)
    └── transcripts/       # Scenario-specific transcripts (optional)
        └── [session].md
```

## Naming Conventions

**Linear Narrative:**
- `act-1-consultation/`
- `act-2-debate/`
- `scene-3-resolution/`
- `chapter-1-introduction/`

**Alternate Realities:**
- `timeline-a-standard/`
- `timeline-b-aggressive/`
- `reality-1-baseline/`
- `reality-2-divergence/`

**Topic-Based:**
- `echopoint-consultation/`
- `monica-meeting/`
- `facility-upgrade-debate/`
- `ai-ethics-roundtable/`

## Creating a New Scenario

1. **Create directory** → `scenarios/[scenario-name]/`
2. **Copy template** → Copy `.template-SCENARIO.yml` to `scenarios/[scenario-name]/SCENARIO.yml`
   - **Note:** Use `scenarios/.template-SCENARIO.yml`, not the root `mg/SCENARIO.yml` (which is legacy)
3. **Create README.md** → Describe the scenario, setup, and narrative context
4. **Configure SCENARIO.yml** → Set:
   - `active_participants` (character file paths)
   - `topic` (what they're discussing)
   - `type` (debate, roundtable, consultation, etc.)
   - `protocol` (optional: `DEBATE`, `ADVERSARIAL-COMMITTEE`, `ROBERTS-RULES`, etc.)
5. **Update SCENARIOS.yml** → (Optional) Register the scenario in `mg/SCENARIOS.yml` for tracking
6. **Run scenario** → LLM simulates dialogue using character files

**See `../BEHAVIORS.md`** for available MOOLLM behaviors you can use in scenarios.

## Character References

Characters are referenced from `../characters/`:
```yaml
active_participants:
  - ../characters/frankie-kerouac.yml
  - ../characters/marcus-chen.yml
```

Or use relative paths from scenario root:
```yaml
active_participants:
  - ../../characters/frankie-kerouac.yml
```

**Important:** Ensure all characters have **debate propensities** defined. Characters without propensities won't debate effectively. See `../characters/README.md` for details.

## Protocols & Behaviors

You can invoke MOOLLM behaviors in your `SCENARIO.yml`:

```yaml
scenario:
  type: debate
  protocol: DEBATE  # or ADVERSARIAL-COMMITTEE, ROBERTS-RULES, etc.
```

See `../BEHAVIORS.md` for:
- **DEBATE** — Structured multi-perspective deliberation
- **ADVERSARIAL-COMMITTEE** — Committee with opposing views
- **ROBERTS-RULES** — Parliamentary procedure
- **SOUL-CHAT** — Free-form conversations
- **SPEED-OF-LIGHT** — Simulate many turns in one call

Mention the protocol name (e.g., `DEBATE`) or structure your scenario accordingly.

