# Sniffable Python

> **"Structure code for the first 50 lines. That's all the LLM needs."**

*If your code smells good, the LLM can sniff it from the first whiff.*

Steve Jobs wanted pixels so beautiful you'd want to lick them. We want code so clear you can sniff its purpose from the header.

Python scripts structured so both humans and LLMs can understand them by reading just the header. But the principle applies to **any language** — good code has an aroma that draws you in from the opening lines. Programming languages are user interfaces. The users are humans and LLMs. Lickable pixels invite visual exploration; sniffable code invites structural exploration.

---

## The MOOLLM Connection

Sniffable Python isn't just a code style — it's **the structural heart of how MOOLLM skills generate and consume automation**.

```
┌─────────────────────────────────────────────────────────────────┐
│                      PLAY-LEARN-LIFT                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   🎮 PLAY           📚 LEARN              🚀 LIFT               │
│   Try things        Document patterns     Automate proven       │
│   Log what happens  Note what works       procedures            │
│       │                   │                    │                │
│       ▼                   ▼                    ▼                │
│   session-log.md →  PROCEDURE.md  →    sister-script.py        │
│                                              │                  │
│                                              ▼                  │
│                                     ┌────────────────────┐      │
│                                     │ SNIFFABLE PYTHON   │      │
│                                     │ ─────────────────  │      │
│                                     │ • Docstring = API  │      │
│                                     │ • main() = CLI     │      │
│                                     │ • Comments = Jazz  │      │
│                                     └────────────────────┘      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

| MOOLLM Concept | How Sniffable Python Serves It |
|----------------|-------------------------------|
| **[play-learn-lift/](../play-learn-lift/)** | The LIFT stage produces sniffable scripts |
| **[sister-script/](../sister-script/)** | Sister scripts ARE sniffable Python |
| **[skill/](../skill/)** | Skills generate sniffable scripts; LLMs sniff them to use |
| **[yaml-jazz/](../yaml-jazz/)** | Comments are semantic data in Python too |
| **[adventure/](../adventure/)** | The linter is a sniffable CLI driving world generation |

---

## Live Example: The Adventure Linter

The [adventure/](../adventure/) skill demonstrates sniffable Python in action. The linter CLI:

1. **Sniffs the adventure world** — reads YAML files, checks consistency
2. **Outputs `LINTER.yml`** — structured findings the LLM can consume
3. **Drives generation** — LLM reads lint output, fixes issues, regenerates content

From [examples/adventure-4/LINTER.yml](../../examples/adventure-4/LINTER.yml):

```yaml
summary:
  rooms_found: 36
  objects_found: 37
  characters_found: 6
  errors: 8
  warnings: 36
  compile_requests: 9
```

**The linter is a sniffable Python script.** The LLM can:
- Sniff its header to understand its CLI
- Run it to get structured output
- Read `LINTER.yml` to understand what needs fixing
- Generate fixes based on the lint events

This creates a **feedback loop**: LLM generates content → linter validates → LLM fixes → iterate.

---

## The Pattern

```python
#!/usr/bin/env python3
"""adventure-lint: Validate adventure world consistency.

Scans adventure directories for ROOM.yml, objects, and characters.
Reports errors, warnings, and suggestions.

Usage:
    python adventure-lint.py lint examples/adventure-4/
    python adventure-lint.py check pub/ROOM.yml
"""

import argparse
from pathlib import Path
import yaml

REQUIRED_FIELDS = ["name", "description", "exits"]  # rooms need these
MAX_EXIT_DEPTH = 10  # prevent infinite loops

def main():
    """CLI structure — the LLM sniffs this to understand the tool."""
    parser = argparse.ArgumentParser(
        description=__doc__.split('\n')[0],
        formatter_class=argparse.RawDescriptionHelpFormatter
    )
    subparsers = parser.add_subparsers(dest="command", required=True)
    
    # lint command — full adventure validation
    lint_parser = subparsers.add_parser("lint", help="Lint entire adventure")
    lint_parser.add_argument("adventure_path", type=Path)
    lint_parser.add_argument("--output", "-o", type=Path, default="LINTER.yml")
    lint_parser.add_argument("--fix", action="store_true", help="Auto-fix simple issues")
    
    # check command — single file validation
    check_parser = subparsers.add_parser("check", help="Check single file")
    check_parser.add_argument("file", type=Path)
    
    args = parser.parse_args()
    _dispatch(args)

# Implementation below the fold — LLM doesn't need to read past here
```

The LLM reads `main()` and knows:
- Two commands: `lint` and `check`
- `lint` takes a path and optional output/fix flags
- `check` validates a single file

**No implementation noise. Pure API. One sniff and you smell success.**

---

## The Skill-Script-Sniff Loop

```
┌──────────────────┐
│   SKILL.md       │  "Here's how to build adventure worlds"
│   (the teacher)  │
└────────┬─────────┘
         │ generates
         ▼
┌──────────────────┐
│  sister-script   │  adventure-lint.py, room-builder.py
│  (the tool)      │  SNIFFABLE PYTHON structure
└────────┬─────────┘
         │ LLM sniffs
         ▼
┌──────────────────┐
│  LLM understands │  Reads first 50 lines
│  (comprehension) │  Knows CLI without running --help
└────────┬─────────┘
         │ uses
         ▼
┌──────────────────┐
│  Output (YAML)   │  LINTER.yml, generated content
│  (structured)    │  LLM-readable results
└────────┬─────────┘
         │ feeds back
         ▼
    [repeat cycle]
```

This is why sniffable Python matters: **it's the code interface between skills and LLMs**.

---

## Concrete World Objects

See these patterns in the wild:

| Object | Location | Why It's Sniffable |
|--------|----------|-------------------|
| **TomTomagotchi** | [kitchen/tomtomagotchi.yml](../../examples/adventure-4/kitchen/tomtomagotchi.yml) | Every ability documented with usage examples |
| **The Pub** | [pub/ROOM.yml](../../examples/adventure-4/pub/ROOM.yml) | Framing protocol explained in comments |
| **The Linter** | [LINTER.yml](../../examples/adventure-4/LINTER.yml) | Structured output LLM can parse |

The TomTomagotchi is a perfect example of YAML Jazz sniffability:

```yaml
abilities:
  COMPASS:
    description: "Point toward a target"
    usage: "COMPASS [target]"
    targets:
      - start     # Always knows home
      - treasure  # The goal
```

**The comment is data.** The LLM reads "Always knows home" and understands the semantics.

---

## Why It Works

| Consumer | Discovery Method |
|----------|------------------|
| Human | `./tool.py --help` |
| LLM | Read first 50 lines |

Same source of truth. No duplicate documentation. No need to hold your nose.

---

## SNIFF CODE — Language-Agnostic Review

The `SNIFF CODE` command reviews **any** source file for sniffability:

| What It Checks | Why It Matters |
|----------------|----------------|
| Purpose at top? | First impression counts |
| API before implementation? | Structure over spelunking |
| Semantic comments? | Comments are data |
| No decorative cruft? | Every token earns its place |

**Good for Python. Good for TypeScript. Good for Go. Good for humans. Good for LLMs.**

The same conventions that make code sniffable for LLMs make it scannable for humans. We're not optimizing for machines at human expense — we're optimizing for **comprehension**, period.

---

## The Intertwingularity

Everything connects. Sniffable Python is the LIFT output of play-learn-lift, the structure of sister-scripts, the interface skills expose to LLMs, and the code pattern that makes the adventure linter feedback loop possible.

```
PLAY-LEARN-LIFT ─────────────────────► sniffable-python (LIFT output)
       │
sister-script ───────────────────────► sniffable-python (the format)
       │
skill ───────────────────────────────► sniffable-python (generated CLI)
       │
yaml-jazz ───────────────────────────► sniffable-python (comments as data)
       │
adventure ───────────────────────────► sniffable-python (linter → feedback)
```

---

## Quick Links

- [SKILL.md](./SKILL.md) — Full specification
- [CARD.yml](./CARD.yml) — Machine-readable interface
- [TEMPLATE.py.tmpl](./TEMPLATE.py.tmpl) — Starter template

## Related Skills

| Skill | Connection |
|-------|------------|
| [play-learn-lift/](../play-learn-lift/) | Sniffable Python is the LIFT stage output |
| [sister-script/](../sister-script/) | Sister scripts follow sniffable conventions |
| [skill/](../skill/) | Skills generate sniffable scripts for LLM use |
| [yaml-jazz/](../yaml-jazz/) | Comments are semantic data |
| [adventure/](../adventure/) | Linter feedback loop exemplifies the pattern |
| [constructionism/](../constructionism/) | Building inspectable things |

## Live Examples

| Example | What It Shows |
|---------|---------------|
| [adventure-4/](../../examples/adventure-4/) | Complete world with linter-driven generation |
| [kitchen/tomtomagotchi.yml](../../examples/adventure-4/kitchen/tomtomagotchi.yml) | YAML Jazz in world objects |
| [pub/ROOM.yml](../../examples/adventure-4/pub/ROOM.yml) | Semantic comments as framing |

---

*"The LLM doesn't need to read your whole file. It needs to read the head and know what the file does."*

*Good code doesn't just avoid bad smells — it has a bouquet that invites exploration.*
