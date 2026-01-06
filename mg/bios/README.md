# 📝 Character Bios

Place your character sketches here as markdown files.

## Bio Format

Your bios can be in any format you prefer — the LLM will extract the relevant information. However, including these elements helps:

### Recommended Structure

```markdown
# Character Name

**Role/Title:** [e.g., "Philosopher", "Scientist", "Politician"]

## Background
[Biography, education, career, key experiences]

## Personality
[Traits, speaking style, mannerisms]

## Beliefs/Positions
[Key positions on topics relevant to your scenarios]

## Relationships
[How they relate to other characters]

## Notable Quotes
[Example quotes that capture their voice]
```

### Minimal Format

Even a simple paragraph works:

```markdown
# Alice

Alice is a pragmatic engineer who believes in iterative solutions.
She speaks in technical terms but tries to make things accessible.
She's skeptical of grand theories and prefers evidence-based approaches.
```

The LLM will extract personality traits, speaking patterns, and beliefs from whatever format you provide.

---

## Transformation Process

When you're ready, tell the LLM:

> "Transform the bios in mg/bios/ into MOOLLM character files in mg/characters/"

The LLM will:
1. Read each bio file
2. Extract personality traits, beliefs, speaking style
3. Create a full MOOLLM character YAML file with:
   - Sims traits or Mind Mirror profile
   - Background and description
   - Beliefs/positions
   - Speaking patterns
   - Relationships
   - Goals

---

## Example

See `example-bio.md` for a sample format (if you create one).

