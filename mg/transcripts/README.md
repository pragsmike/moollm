# 📜 Transcripts

Dialogue transcripts from character interactions are saved here.

**Note:** Transcripts can be stored in two places:
- **Shared transcripts** → This directory (`mg/transcripts/`)
- **Scenario-specific transcripts** → `scenarios/[scenario-name]/transcripts/`

Use scenario-specific transcripts for better organization, or shared transcripts for cross-scenario analysis.

## Format

Each transcript is a markdown file containing:
- Scenario metadata (date, participants, topic)
- Full dialogue with speaker attribution
- Stage directions/narration (if any)
- Summary of key points

## Naming

Use descriptive names:
- `ai-ethics-debate-2026-01-06.md`
- `climate-policy-roundtable-round-1.md`
- `philosophy-symposium-kant-vs-nietzsche.md`

## Structure

```markdown
# Scenario Title

**Date:** 2026-01-06
**Participants:** Alice, Bob, Charlie
**Topic:** [Topic of discussion]
**Type:** Debate / Roundtable / Interview / etc.

---

## Dialogue

**Alice:** [Opening statement]

**Bob:** [Response]

**Charlie:** [Counterpoint]

...

---

## Summary

Key points:
- Point 1
- Point 2

Agreements:
- Consensus item 1

Disagreements:
- Conflict point 1
```

Transcripts are automatically generated during scenario runs and can be edited/annotated afterward.

## What Gets Captured

Transcripts capture:
- **Full dialogue** with speaker attribution
- **Character propensities in action** (how different perspectives play out)
- **Key points** raised by each character
- **Agreements and disagreements** that emerge
- **Final positions** (for structured debates)

The LLM uses character propensities to ensure each character challenges from their unique angle, creating comprehensive exploration of the topic.

