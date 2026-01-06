# 📋 Scenarios

Individual scenario directories live here.

Each scenario is a self-contained interaction with its own:
- **SCENARIO.yml** — State file (participants, topic, dialogue state)
- **README.md** — Description, setup, narrative context
- **transcripts/** (optional) — Scenario-specific transcripts

## Structure

```
scenarios/
├── [scenario-name]/
│   ├── README.md          # Scenario description and setup
│   ├── SCENARIO.yml       # Scenario state (participants, topic, etc.)
│   └── transcripts/       # Scenario-specific transcripts (optional)
│       └── [session].md
└── ...
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

1. Create directory: `scenarios/[scenario-name]/`
2. Copy `SCENARIO.yml` template from `mg/SCENARIO.yml`
3. Create `README.md` with scenario description
4. Update `mg/SCENARIOS.yml` to register the new scenario
5. Set active participants in `SCENARIO.yml`

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

