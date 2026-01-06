# 👥 Characters

MOOLLM-formatted character files live here.

These files are **generated from bios** in `../bios/` and contain:
- Full personality profiles (Sims traits, Mind Mirror)
- Background and biography
- **Debate propensities** (type, risk tolerance, epistemology)
- Beliefs and positions on topics
- Speaking style and vocabulary
- Relationships with other characters
- Goals and motivations

## Format

Each character file follows the MOOLLM character format (see `examples/adventure-3/characters/don-hopkins.yml` for reference), adapted for dialogue scenarios:

```yaml
character:
  name: "Character Name"
  id: character-id
  type: participant  # or debater, panelist, etc.
  
  description: |
    Brief description of the character
    
  background: |
    Full biography
    
  personality:
    # Sims traits or Mind Mirror profile
    
  beliefs:
    topic-1: "Position on topic 1"
    topic-2: "Position on topic 2"
    
  speaking_style:
    vocabulary: []
    patterns: []
    tone: ""
    
  relationships:
    other-character:
      closeness: 5
      trust: 6
      # ...
  
  propensity:
    type: operational_realism  # e.g., paranoid_realism, idealism, evidence_prosecutor
    risk_tolerance: medium     # low, medium, high, varies
    epistemology: prove_it     # assume_bad_faith, assume_good_faith, trust_precedent, prove_it, trace_feedback_loops
    
    surfaces:
      - "Operational risks and failure modes"
      - "What happens when systems break at 2 a.m."
    
    voice: "Okay, but what happens at 2 a.m. when this breaks?"
    
    debate_role: operational_reality_check  # devil's_advocate, opportunity_scout, historian, etc.
```

## Debate Propensities

All characters include **explicit propensities** that make them effective participants in adversarial committee debates.

### Why Propensities Matter

According to the **adversarial-committee** skill, propensities are crucial because they:
1. **Force genuine debate** — incompatible values create real conflict
2. **Surface blind spots** — each propensity reveals different hidden assumptions
3. **Prevent premature consensus** — characters with different epistemologies won't agree too quickly
4. **Enable structured exploration** — you know what each character will challenge

### Benefits

1. **Structured Debate** — LLM knows exactly what each character will challenge
2. **Wide Exploration** — Different epistemologies force exploration of different angles
3. **Prevents Groupthink** — Incompatible values prevent premature consensus
4. **Predictable Behavior** — You can design scenarios knowing how characters will react
5. **Calibration** — Can tune propensities if debates are too conflict-heavy or too consensus-driven

### Example Debate

**Scenario:** "Should we adopt AI coding assistant X?"

- **Samir** (operational_realism): "What's the rollback plan? How do we test this?"
- **Elena** (compliance_guardian): "Show me the source for that security claim."
- **Derrick** (opportunity_optimist): "This could help us move faster—how do we make it true?"
- **Patricia** (delivery_realist): "How will this show up in delivery? What's the actual commitment?"
- **Jordan** (pedagogical_experimenter): "How would we teach this? What's the safe way to learn?"
- **Ravi** (evidence_architect): "What's our evidence this works? How do we measure it?"

Each character challenges from a different angle, forcing comprehensive exploration.

## Generation

These files are created by transforming bios. Tell the LLM:

> "Transform mg/bios/*.md into MOOLLM character files in mg/characters/"

The LLM will read each bio and create a full character file with all necessary fields, including propensities.

## Evaluation

See [../CHARACTER-RUBRIC.md](../CHARACTER-RUBRIC.md) for how to score character sheets for debate effectiveness, and [../CHARACTER-SCORES.md](../CHARACTER-SCORES.md) for current character scores.

