---
name: room
description: "Directories as activation contexts. Entering = calling. Exiting = returning."
license: MIT
tier: 1
allowed-tools:
  - read_file
  - write_file
related: [card, adventure, memory-palace, character, world-generation, data-flow, naming]
---

# Room

> **Directories as activation contexts. Entering = calling. Exiting = returning.**

The filesystem becomes a navigable world. Cards come alive when you enter their room.

## The Metaphor

| Filesystem | Simulation | Programming |
|------------|------------|-------------|
| Directory | Room | Stack frame |
| `cd room/` | Enter | Function call |
| `cd ..` | Exit | Return |
| Files in dir | Active entities | Local variables |
| Links | Exits/doors | Calls to other functions |

## Room Anatomy

```
room-name/
├── ROOM.yml        # Room definition
├── README.md       # Room's voice (optional)
├── CARD.yml        # Card sidecar (optional)
├── character-*.yml # NPCs embedded in room
├── object-*.yml    # Objects in room
└── nested-room/    # Sub-room
```

## ROOM.yml Structure

```yaml
room:
  name: "The Pub"
  purpose: "Social hub and quest giver"
  
  context:
    - "Cozy Dutch coffeeshop atmosphere"
    - "Marieke tends bar"
    
  exits:
    street: "../street/"
    cat_cave: "./cat-cave/"
    back_door: "../alley/"
    
  occupants:
    - budtender-marieke.yml
    - cat-terpie.yml
    
  working_set:  # Auto-load when entering
    - "ROOM.yml"
    - "budtender-marieke.yml"
```

## Exits & Navigation

```yaml
exits:
  # Named exits
  north: "../forest/"
  east: "../town/"
  
  # Semantic exits
  home: "~/characters/don-hopkins/"  # Absolute
  parent: "../"                       # Relative
  
  # Conditional exits
  secret_door:
    target: "../treasure-room/"
    condition: "has_key == true"
    hidden: true  # Not shown until discovered
```

## Nested Rooms & Virtual Zones

Rooms can contain rooms. Virtual zones don't need subdirectories:

```yaml
# cat-cave.yml — TARDIS-like nested room
id: cat-cave
type: [room, furniture]  # Both!

zones:  # Virtual sub-rooms (no physical directories)
  nap-zone:
    description: "Sunny spot, cushions everywhere"
    path: "pub/cat-cave/nap-zone"  # Virtual path
  box-jungle:
    description: "Cardboard paradise"
    path: "pub/cat-cave/box-jungle"
```

Characters reference virtual zones:

```yaml
# cat-terpie.yml
home: pub/cat-cave/
location: pub/cat-cave/nap-zone  # Virtual zone
```

## Home vs Location Protocol

Entities have **home** (where file lives) and **location** (where they are):

```yaml
character:
  home: pub/cat-cave/terpie.yml     # File never moves
  location: pub/                     # Currently in pub
```

Movement updates `location`, not file. See [character/](../character/).

## Room Relationships

Rooms can remember visitors:

```yaml
relationships:
  don-hopkins:
    visits: 3
    reputation: "regular"
    memory: "Always nice to the cats"
```

## NPC Embedding Patterns

| Pattern | When | Example |
|---------|------|---------|
| `cat-name.yml` | Embedded NPC | `pub/cat-terpie.yml` |
| `name/CHARACTER.yml` | Complex character | `characters/don-hopkins/` |
| `staff-name.yml` | Role-based grouping | `pub/staff-marieke.yml` |

See [naming/](../naming/) for conventions.

## Working Set

When entering a room, load:
1. `ROOM.yml` — the room itself
2. `README.md` — room's voice (if exists)
3. Occupant files listed in `occupants:`
4. Anything in `working_set:`

## Related Concepts

| Concept | Skill | Relationship |
|---------|-------|--------------|
| Nested rooms | This skill | Rooms in rooms |
| Throwing objects | [data-flow/](../data-flow/) | Rooms as nodes, objects as messages |
| Instant communication | [speed-of-light/](../speed-of-light/) | Multi-entity simulation per turn |
| Multi-instantiation | [multi-presence/](../multi-presence/) | Same card in multiple rooms |
| Room as mnemonic | [memory-palace/](../memory-palace/) | Spatial knowledge organization |

## Live Examples

- [examples/adventure-3/pub/](../../examples/adventure-3/pub/) — A room with NPCs
- [examples/adventure-3/pub/cat-cave.yml](../../examples/adventure-3/pub/cat-cave.yml) — Nested room with zones

## Dovetails With

### Sister Skills
- [card/](../card/) — What lives in rooms
- [character/](../character/) — Home vs location
- [naming/](../naming/) — File organization
- [data-flow/](../data-flow/) — Rooms as processing nodes

### Kernel
- [kernel/context-assembly-protocol.md](../../kernel/context-assembly-protocol.md) — Working set loading
