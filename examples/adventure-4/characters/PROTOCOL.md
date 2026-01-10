# Character Directory — Adventure 4

> *"READMEs are catalogs. Subdirectories are incarnations."*

**For the generic character skill, see:** [skills/character/](../../../skills/character/)

---

## This Directory's Structure

```
characters/
├── PROTOCOL.md           # This file
├── abstract/             # Templates and prototypes
│   └── player/           # Base player character template
├── fictional/            # Original fictional characters
│   ├── bumblewick-fantastipants/
│   └── donna-toadstool/  # The Mushroom Queen
├── real-people/          # Real people (with consent/ethical framing)
│   └── don-hopkins/
├── animals/              # Cats, dogs, creatures
│   ├── biscuit/
│   └── palm/
└── robots/               # AI, robots, synthetic entities
```

---

## Adventure-Specific Conventions

### Two-Level Pattern (Catalogs + Incarnations)

- **README.md** in each subdirectory lists POSSIBLE characters (lazy/uninstantiated)
- **Subdirectories** are ACTUAL characters (instantiated)

### Just-In-Time Incarnation

Characters are created when needed:

```
> INCARNATE alan-kay

Created: characters/real-people/alan-kay/CHARACTER.yml
```

### Uniqueness

Each incarnation is **unique to this adventure**. Same reference source, different instance.

---

## Core Principles (from generic skill)

**See [skills/character/SKILL.md](../../../skills/character/SKILL.md) for:**

- **Home vs Location** — File path vs world position
- **Character State Ownership** — CHARACTER.yml is CANONICAL
- **Inventory (Bidirectional)** — References, not file moves
- **Relationships** — Key-value feelings map
- **Sims Traits & Mind Mirror** — Personality systems

The generic skill defines the patterns. This directory applies them.

---

## Sub-Category Promotion

When a README section grows, promote to subdirectory with ROOM.yml.

---

## Ethical Inheritance

Subdirectories inherit ethics from parents. Can add constraints, not remove.

> *"The README is the seed catalog. The subdirectory is the garden."*
