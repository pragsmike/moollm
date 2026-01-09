# PR: Character Organization & Ethical Framework Enhancement

**Date:** 2026-01-09  
**Branch:** don-adventure-4-run-1  
**Author:** Claude (with Don Hopkins)

---

## Summary

Major reorganization of character system with enhanced ethical declarations, startup hook implementation, and navigation fixes.

---

## Changes

### 1. Character Directory Structure

Characters are now organized into ethical categories:

```
characters/
├── abstract/          # Conceptual beings, player prototypes
│   └── player/        # The generic hero template
├── real-people/       # Living and deceased real humans
├── fictional/         # Characters from fiction, games, TV
├── animals/           # Real and fictional animals
└── robots/            # Mechanical minds, AIs
```

**Convention clarified:**
- **Directory characters** (e.g., `characters/abstract/player/`) → show directory path when describing self; implicitly contain `CHARACTER.yml`
- **File-only characters** (e.g., `biscuit.yml` inside an owner's directory) → show file path

### 2. Enhanced Ethical Declarations

Each character category now has comprehensive ethical framing in their `ROOM.yml`:

| Category | Protocol | Key Addition |
|----------|----------|--------------|
| `real-people/` | TRIBUTE | Living vs deceased guidelines, abstraction levels, The Sims precedent |
| `fictional/` | CREATIVE | Fan tradition context, fair use principles, legal awareness |
| `abstract/` | CONCEPTUAL | Player prototype explanation, incarnation rights for abstracts |
| `animals/` | CREATURE | Real animals get tribute-level respect, species wisdom |
| `robots/` | ARTIFICIAL | Modern AI simulation distinction, philosophical territory |

All rooms now explicitly reference `skills/representation-ethics/` and `skills/incarnation/`.

### 3. Startup Hook System

New `startup.yml` at project root:
- Configurable post-boot behavior
- Delegates to `adventure:RESUME` or `adventure:START`
- Character generation if none exists
- Override with `startup.local.yml` (gitignored)

New methods added:
- `bootstrap:STARTUP` — reads startup.yml, dispatches to mode
- `adventure:RESUME` — continue where left off
- `adventure:START` — fresh game with character generation
- `adventure:ENSURE-CHARACTER` — make sure player exists
- `adventure:CREATE-CHARACTER` — generate from prototype

### 4. Navigation Fixes

Verified canonical layout from `start/ROOM.yml`:
- **WEST** → kitchen
- **EAST** → coatroom

The coatroom is now a transformation hub with exits:
- **WEST** → start (Chamber of Commencement)
- **NORTH** → characters (Hall of Bodies)
- **SOUTH** → personas (Wardrobe of Masks)
- **EAST** → skills (Skill Nexus)

### 5. Anti-Pattern: ASCII Maps

Added explicit prohibition in `skills/room/CARD.yml`:
- ASCII art maps are FORBIDDEN
- LLM indentation is unreliable
- High token cost, high maintenance
- Use markdown tables instead

---

## Files Changed

### New Files
- `startup.yml` — Session startup configuration
- `examples/adventure-4/skills/ROOM.yml` — Skill Nexus room
- `examples/adventure-4/skills/README.md` — Skill Nexus documentation
- `documents/PR-2026-01-09-character-reorganization.md` — This PR note

### Modified Files
- `skills/bootstrap/CARD.yml` — Added STARTUP method
- `skills/adventure/CARD.yml` — Added RESUME, START, ENSURE-CHARACTER, CREATE-CHARACTER
- `skills/room/CARD.yml` — Added anti-patterns section (no ASCII maps)
- `PROTOCOLS.yml` — Added new K-lines
- `examples/adventure-4/ADVENTURE.yml` — Updated character paths
- `examples/adventure-4/characters/ROOM.yml` — Updated navigation
- `examples/adventure-4/characters/README.md` — Directory vs file convention
- `examples/adventure-4/characters/*/ROOM.yml` — Enhanced ethical declarations (all 5)
- `examples/adventure-4/coatroom/ROOM.yml` — Updated exits and references
- `examples/adventure-4/coatroom/README.md` — Updated navigation and character paths
- `examples/adventure-4/coatroom/mannequin.yml` — Updated character references
- `examples/adventure-4/personas/ROOM.yml` — Added navigation links
- `examples/adventure-4/LOG.md` — Updated player path
- `examples/adventure-4/TRANSCRIPT.md` — Updated player path

---

## Breaking Changes

- Character paths changed from `characters/player/` to `characters/abstract/player/`
- All references updated, but external tools pointing to old paths will need updating

---

## Testing Notes

- Verified navigation links between coatroom ↔ characters/personas/skills
- Verified all character subdirectory ethical declarations load correctly
- Startup hook is designed but not yet integrated into bootstrap execution

---

## Related Skills

- `skills/representation-ethics/` — Full ethical framework
- `skills/incarnation/` — Character autonomy principles
- `skills/room/` — Room navigation and building

---

## Quotes

> "You ARE your file." — MOOLLM character philosophy

> "DO NOT create ASCII art maps!" — skills/room/CARD.yml anti-patterns

> "Animals are not objects. They have inner lives." — animals/ROOM.yml
