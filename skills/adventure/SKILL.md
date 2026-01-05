---
name: adventure
description: Room-based exploration with narrative evidence collection
allowed-tools:
  - read_file
  - write_file
  - list_dir
tier: 1
protocol: ADVENTURE
tags: [exploration, narrative, investigation, game]
lineage: "Colossal Cave, Zork, MUD, LambdaMOO"
inherits: simulation
related: [room, card, session-log, simulation, party, character]
templates:
  - file: ADVENTURE.yml.tmpl
    purpose: Complete adventure state (inherits simulation properties)
  - file: LOG.md.tmpl
    purpose: Narrative journal
---

# Adventure

> *"Every directory is a room. Every file is a clue. Navigation is investigation."*

**Inherits from:** [simulation/](../simulation/) — all simulation properties plus adventure-specific state.

**Lineage:** Colossal Cave, Zork, MUD, LambdaMOO.

## The Premise

Directories = rooms. Files = clues/characters/objects. The LLM dungeon masters you around.

```yaml
player:
  character: characters/alice/
  location: entrance-hall/
  
party:
  members: [characters/alice/]
  leader: characters/alice/
```

## Core Loop

```
User: "go north"
  → DM updates player.location, describes room
User: "look around"  
  → DM reads ROOM.yml, narrates
User: "take rusty key"
  → DM moves key to inventory, narrates
```

## Key Mapping

| Filesystem | Adventure |
|------------|-----------|
| Directory | Room |
| Files in dir | Clues, NPCs, objects |
| `ADVENTURE.yml` | World state |
| `README.md` | Narrative transcript |
| Chat | Player commands |
| LLM | Dungeon Master |

## ADVENTURE.yml

```yaml
# Inherits all simulation/ properties, plus:

adventure:
  name: "The Lost Artifact"
  objective: "Find the ancient gem"
  status: active

navigation:
  starting_room: entrance/
  current_room: library/
  rooms_visited:
    - path: entrance/
      entered: "2024-01-05"

evidence:
  clues: []
  items: []
  characters_met: []

quest_log:
  - "2024-01-05: Entered the dungeon"
```

See [ADVENTURE.yml.tmpl](./ADVENTURE.yml.tmpl) for full template.

## Commands

| Command | Effect |
|---------|--------|
| `GO [direction]` | Navigate |
| `LOOK` | Describe room |
| `EXAMINE [thing]` | Inspect object/NPC |
| `TAKE [object]` | Add to inventory |
| `TALK TO [npc]` | Start conversation |
| `USE [object]` | Interact |
| `INVENTORY` | List held items |
| `MAP` | Show visited rooms |

## Multi-Character Adventures

Adventures support multiple characters via [party/](../party/) and selection:

```yaml
party:
  members:
    - characters/alice/
    - characters/bob/
  leader: characters/alice/

selection:
  targets: [characters/alice/]  # Commands go here
```

| Selection | Effect |
|-----------|--------|
| `SELECT alice` | Control Alice |
| `SELECT alice, bob` | Control both |
| `CYCLE` | Next character |

## Evidence Collection

```yaml
evidence:
  clues:
    - id: clue-001
      found_in: library/ancient-tome.yml
      content: "The gem glows at midnight"
      significance: high
      
  items:
    - name: "Rusty Key"
      path: entrance/rusty-key.yml
      acquired: "2024-01-05"
```

## Codebase Archaeology

Adventures work for code exploration too:

```
entrance/           → repo root
library/            → src/
tests/              → tests/
ancient-tome.yml    → README.md
clue-001            → "Bug introduced in commit abc123"
```

## Future: Python CLI

Deterministic operations (YAML parsing, movement, validation) could be Python. LLM focuses on narration and reasoning.

```bash
$ adventure move alice north      # Python handles coordinates
$ adventure lint quest/           # Python validates schemas
# → LLM narrates the results
```

## Live Examples

- [examples/adventure-3/](../../examples/adventure-3/) — Full adventure instance
- [examples/adventure-3/ADVENTURE.yml](../../examples/adventure-3/ADVENTURE.yml) — State file
- [examples/adventure-3/pub/](../../examples/adventure-3/pub/) — Room with NPCs

## Dovetails With

### Sister Skills
- [simulation/](../simulation/) — Base class (adventure inherits this)
- [room/](../room/) — Navigation
- [party/](../party/) — Multi-character
- [character/](../character/) — Player/NPC definitions
- [session-log/](../session-log/) — Transcript

### Kernel
- [kernel/context-assembly-protocol.md](../../kernel/context-assembly-protocol.md) — Working set loading
