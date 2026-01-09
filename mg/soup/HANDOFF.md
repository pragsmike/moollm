# Handoff: Soup House Session

**Date**: 2025-01-09
**Session Goal**: Design a house ("soup") where rooms represent projects, with automatic context loading when entering rooms.

---

## What We Built

A house at `mg/soup/` with five rooms:

```
mg/soup/
├── HOUSE.yml           # House metadata, floor plan, teleport system
├── entryway/ROOM.yml   # Front door, transitional
├── living-room/ROOM.yml # Central hub
├── kitchen/ROOM.yml    # Resource management (has objects)
├── library/ROOM.yml    # Reference materials
└── workshop/ROOM.yml   # Active work area
```

The **kitchen** has populated objects: `refrigerator.yml`, `pantry.yml`, `counter.yml`, `shopping-list.yml`. Other rooms have placeholder objects commented in their `working_set:`.

---

## Mistakes I Made (Learn From These)

### 1. Invented `context:` when `working_set:` already existed

I created a new structure:
```yaml
context:
  local: [...]
  references: [...]
  space: { name: "..." }
```

This was wrong. The room skill already defines `working_set:` for exactly this purpose:
```yaml
working_set:
  - ROOM.yml
  - state/progress.yml
```

**Lesson**: Before inventing new YAML structures, search the existing codebase. Use `Grep` to find how similar concepts are already handled.

### 2. Proposed modifying core files (hot.yml) unnecessarily

I suggested adding room-based triggers to `hot.yml`. The user wisely pushed back: "when I see that we think we need to change one of the core files, I wonder if we're just missing something."

They were right. The room's `working_set:` is the source of truth. The orchestrator reads it directly — no need to duplicate in `hot.yml`.

**Lesson**: MOOLLM is well-designed. If you think you need to modify kernel files or core infrastructure, step back and look for existing patterns first.

### 3. Invented `context_model: replace` in HOUSE.yml

I added this to specify that room contexts replace rather than stack. But this isn't a MOOLLM convention — it was my invention with no backing infrastructure.

**Lesson**: Don't add configuration for behavior that isn't implemented. If you're not sure how something works, ask or research rather than inventing.

---

## Key MOOLLM Patterns Discovered

### Room Context Loading

Rooms declare their context via `working_set:`:
```yaml
room:
  name: Kitchen
  working_set:
    - ROOM.yml
    - refrigerator.yml
    - pantry.yml
```

The global `working_set.yml` tracks current state:
```yaml
focus:
  room: mg/soup/kitchen/   # Current location
  task: null
  character: null
  skill: null
```

### Memory Management

- `hot.yml` — what SHOULD be loaded (with triggers)
- `cold.yml` — what was evicted (with recovery hints)
- `working_set.yml` — what IS loaded right now

These work together. The room's `working_set:` feeds into this system.

### Files to Study

Before extending MOOLLM, read these:
- `skills/room/SKILL.md` — the room metaphor and ROOM.yml structure
- `skills/room/ROOM.yml.tmpl` — template showing standard fields
- `kernel/context-assembly-protocol.md` — how files get loaded
- `kernel/memory-management-protocol.md` — hot/cold/working_set flow

---

## What Works Now

1. **Navigation**: Rooms have `exits:` connecting them physically
2. **Teleport**: `HOUSE.yml` defines a teleport system for direct access
3. **Working sets**: Each room declares what files to load via `working_set:`
4. **Kitchen objects**: Refrigerator (perishables), pantry (stable supplies), counter (active use), shopping list (to acquire)

---

## Open Questions

### How does context actually get loaded?

The `working_set:` declares intent, but what executes it? Options:

1. **Custom orchestrator** — reads room's working_set, injects files into prompt
2. **LLM follows protocol** — when user says "TELEPORT kitchen", the LLM reads the files as a convention
3. **Claude Projects / Cursor contexts** — manual mapping, room = project

Currently, MOOLLM is a specification. The orchestrator behavior is defined but not all implementations exist.

### Replace vs. Stack?

When entering a new room, does its context:
- **Replace** the previous room's context (one room at a time)
- **Stack** on top (nested contexts)

The user said "replace" but we removed that config since it wasn't a MOOLLM convention. This behavior would be determined by the orchestrator, not declared in YAML.

---

## Suggested Next Steps

### 1. Populate other rooms
Library needs: `shelves.yml`, `card-catalog.yml`
Workshop needs: `workbench.yml`, `tool-rack.yml`, `materials-bin.yml`

### 2. Test the workflow
Actually use soup house for a real project:
- Add real file references to a room's `working_set:`
- See if the metaphor helps organize work

### 3. Implement TELEPORT behavior
When user says "TELEPORT kitchen":
1. Update `working_set.yml` with `focus.room: mg/soup/kitchen/`
2. Read the room's `working_set:` files
3. Present room description

This could be a skill or just a protocol the LLM follows.

### 4. Study existing adventures
Look at `examples/adventure-3/` and `examples/adventure-4/` to see how rooms work in practice. Do they use `working_set:`? How do they handle context?

---

## Summary

**The main lesson**: MOOLLM is thoughtfully designed. When you think you need something new, you're probably missing an existing pattern. Search before inventing. The room skill already had `working_set:` — I just didn't see it until the user pushed back on my invented `context:` structure.

Trust the existing conventions. Extend them, don't replace them.
