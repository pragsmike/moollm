# Memory Palace Skill
## Spatial Organization of Knowledge in Navigable Directories

*"The filesystem is the mind. Directories are rooms. Files are objects."*

---

## Purpose

Transform complex information into a navigable spatial structure where:
- **Directories** = Rooms/locations you can visit
- **Files** = Objects/artifacts you can examine
- **Links** = Doors/passages between spaces
- **`.meta.yml`** = Sticky notes on the wall

This leverages the ancient "method of loci" memory technique, adapted for LLMs navigating filesystems.

---

## When to Use

- Organizing a large research project
- Building a knowledge base that grows over time
- Creating a "second brain" for a domain
- Exploring complex topics systematically
- Maintaining context across sessions

---

## Prerequisites

- File tools (ls, read, write, mkdir)
- No execution required (Tier 1)

---

## Protocol

### Step 1: Create the Palace

1. Establish a root directory for the palace
2. Create an ENTRY.md as the "front door"
3. Create initial rooms based on major themes

```
palace/
├── ENTRY.md              # Welcome, orientation, map
├── MAP.yml               # Navigation structure
├── room-name/
│   ├── ROOM.md           # Room description
│   ├── artifact.md       # Something in the room
│   └── artifact.meta.yml # Notes about it
```

### Step 2: Navigate and Populate

1. Enter a room by reading its ROOM.md
2. Examine artifacts by reading files
3. Leave notes by creating/updating .meta.yml
4. Create new rooms as topics emerge
5. Link rooms through explicit references

### Step 3: Maintain the Palace

1. Update MAP.yml as structure grows
2. Add cross-references between rooms
3. Archive stale rooms to attic/
4. Create summary files for dense rooms

---

## Core Files

### ENTRY.md
```markdown
# Palace Name

## Welcome
What this palace contains and why.

## Quick Navigation
- [Room A](room-a/ROOM.md) - Description
- [Room B](room-b/ROOM.md) - Description

## Recent Activity
- Added X to Room A
- Created new Room C

## How to Use
Instructions for navigating this palace.
```

### MAP.yml
```yaml
palace:
  name: "Research Palace"
  created: "2025-12-30"
  
rooms:
  - name: "foundations"
    path: "foundations/"
    description: "Core concepts"
    connects_to: ["applications", "history"]
    
  - name: "applications"
    path: "applications/"
    description: "Practical uses"
    connects_to: ["foundations", "examples"]

landmarks:
  - name: "The Big Question"
    location: "foundations/core-question.md"
    importance: "Start here"
```

### ROOM.md (in each room)
```markdown
# Room Name

## What's Here
Description of this room's contents.

## Artifacts
- [artifact-1.md](artifact-1.md) - Description
- [artifact-2.md](artifact-2.md) - Description

## Doors
- ← Back to [Entry](../ENTRY.md)
- → Forward to [Next Room](../next-room/ROOM.md)
- ↓ Down to [Sub-room](sub-room/ROOM.md)

## Notes
Observations, questions, TODOs for this room.
```

---

## Navigation Commands

When using the Memory Palace, think spatially:

| Intent | Action |
|--------|--------|
| "Enter the palace" | Read ENTRY.md |
| "Look around" | ls current directory |
| "Go to room X" | cd to room, read ROOM.md |
| "Examine artifact" | Read the file |
| "Leave a note" | Create/update .meta.yml |
| "Create new room" | mkdir + create ROOM.md |
| "Check the map" | Read MAP.yml |
| "Where am I?" | Note current path |

---

## Tips

1. **Start small** — Begin with 3-5 rooms, expand as needed
2. **Name meaningfully** — Directory names are addresses
3. **Link generously** — Cross-references aid recall
4. **Leave breadcrumbs** — Update .meta.yml as you explore
5. **Maintain the map** — MAP.yml is your table of contents
6. **Archive, don't delete** — Move stale rooms to attic/

---

## Example: Research Palace

```
research-palace/
├── ENTRY.md
├── MAP.yml
├── foundations/
│   ├── ROOM.md
│   ├── key-concepts.md
│   ├── key-concepts.meta.yml
│   └── terminology.md
├── literature/
│   ├── ROOM.md
│   ├── paper-summaries/
│   └── key-quotes.md
├── experiments/
│   ├── ROOM.md
│   ├── experiment-1/
│   └── experiment-2/
├── synthesis/
│   ├── ROOM.md
│   ├── findings.md
│   └── open-questions.md
└── attic/
    └── abandoned-ideas/
```

---

## Outputs

- A navigable directory structure
- ENTRY.md as the palace front door
- MAP.yml for orientation
- Populated rooms with artifacts and notes
