---
name: cat
description: Feline interactions, buffs, and relationship building
allowed-tools:
  - read_file
  - write_file
tier: 1
protocol: CAT
tags: [pet, companion, interaction, buff]
related: [character, buff, mind-mirror, room]
---

# CAT — Feline Interactions

> *"Cats are the original NPCs. They have their own agenda."*

Cats are gameplay, not decoration. Each cat overlays this skill with its personality.

## Interaction Pattern

All cat interactions follow this structure:

```yaml
INTERACTION:
  command: "VERB [cat]"
  risk: low | medium | high
  
  success_calculation: |
    Based on cat's Sims traits (Nice, Playful, Outgoing, Active)
    plus relationship level plus knowledge of cat's preferences
    
  outcomes:
    success:
      buff: "+N trait for duration"
      message: "*cat behavior*"
    failure:
      debuff: "penalty"
      learning: "what you learned"
```

## Interaction Types

### Touch Interactions

| Command | Risk | Key Trait | Notes |
|---------|------|-----------|-------|
| `PAT [cat]` | Low | Nice | Quick, safe |
| `PET [cat]` | Medium | Nice+Outgoing | Extended contact |
| `SCRITCH [cat]` | Medium | Playful | Requires knowing preferences |
| `BELLY RUB [cat]` | **HIGH** | Nice ≥7 | The forbidden zone |
| `PICK UP [cat]` | Medium | Nice+Trust | Some cats hate it |

### Play Interactions

| Command | Risk | Key Trait | Notes |
|---------|------|-----------|-------|
| `PLAY WITH [cat]` | Low | Playful | General engagement |
| `LASER POINTER` | Low | Active | End with a "catch" or cause existential crisis |
| `FEATHER TOY` | Low | Playful+Active | Classic |
| `STRING` | Medium | Playful | Supervised only |

### Social Interactions

| Command | Risk | Key Trait | Notes |
|---------|------|-----------|-------|
| `TALK TO [cat]` | None | Outgoing | They judge your tone |
| `OBSERVE [cat]` | None | — | Learn preferences |
| `OFFER TREAT [cat]` | Low | — | Food is universal |
| `INVITE [cat]` | Low | Outgoing | Ask to join party |

## Example: PAT

```yaml
PAT:
  command: "PAT [cat]"
  risk: low
  duration: brief
  
  success_calculation: |
    success_chance = (cat.nice + cat.outgoing) / 20
    # Nice 8 + Outgoing 6 = 70% success
    
  outcomes:
    success:
      buff: "+1 Cheerful (5 min)"
      message: "*purrs briefly*"
    neutral:
      message: "*tolerates it*"
    failure:
      debuff: "-1 next interaction"
      message: "*ear flicks irritably*"
```

## Example: BELLY RUB (High Risk)

```yaml
BELLY_RUB:
  command: "RUB [cat]'S BELLY"
  risk: HIGH
  
  success_calculation: |
    success = (cat.nice - 5) / 10
    if cat.nice < 7: almost_guaranteed_failure
    
  outcomes:
    success:
      buff: "+5 bond, cat follows you"
      message: "*allows the forbidden touch*"
    trap:
      damage: "1d4 scratch (cosmetic)"
      message: "*CLAMP* *bunny kicks*"
      learning: "This cat is NOT a belly cat"
```

## Buff System

Cat interactions grant buffs. See [buff/](../buff/) for full system.

| Effect | Duration | Source |
|--------|----------|--------|
| Cheerful +1-3 | 5-30 min | Most positive interactions |
| Calm +1-2 | 15-60 min | Purring cats |
| Playful +2 | 15 min | Play sessions |
| Lucky | Varies | Special cats (terpene buffs) |

## Cat Instance Pattern

Each cat file overlays this skill:

```yaml
# pub/cat-terpie.yml
id: terpie
type: [cat, character]
home: pub/cat-cave/
location: pub/cat-cave/nap-zone

sims_traits:  # Affects interaction success
  nice: 5
  outgoing: 4
  active: 3
  playful: 6
  neat: 2
  
personality:  # Affects roleplay
  quirks: ["judges silently", "knows things"]
  preferences:
    scritch_spots: [chin, ears]
    dislikes: [belly rubs, sudden movements]
    
buffs:  # What THIS cat grants
  terpie_blessing:
    effect: "Lucky breaks for 1 hour"
    trigger: successful_deep_interaction
```

## Cat Cave Pattern

Cats can cluster in nested rooms:

```yaml
# pub/cat-cave.yml
id: cat-cave
type: [room, furniture]  # Both!

zones:
  nap-zone: "Sunny spot, cushions"
  box-jungle: "Cardboard paradise"

occupants:  # Cats defined in separate files
  - cat-terpie.yml
  - cat-stroopwafel.yml
```

See: [examples/adventure-3/pub/](../../examples/adventure-3/pub/)

## Dovetails With

### Sister Skills
- [character/](../character/) — Cats ARE characters
- [buff/](../buff/) — Interaction effects
- [mind-mirror/](../mind-mirror/) — Personality traits

### Live Examples
- [examples/adventure-3/pub/cat-terpie.yml](../../examples/adventure-3/pub/cat-terpie.yml)
- [examples/adventure-3/pub/cat-cave.yml](../../examples/adventure-3/pub/cat-cave.yml)
