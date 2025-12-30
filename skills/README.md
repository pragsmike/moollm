# MOOLLM Skills
## Userland Protocols Over Files

*"Skills are conventions the model follows, not code the orchestrator runs."*

---

## What is a Skill?

A skill is a **userland protocol** that defines:
- Directory layouts and naming conventions
- File formats and schemas
- Behavioral rules and checklists
- Interaction patterns

Skills are implemented purely through:
- File tools (ls, read, write, patch)
- Search tools (lexical, vector)
- The model following documented rules

**Skills do NOT require orchestrator changes.**

---

## Skill Tiers

| Tier | Tools Required | Examples |
|------|----------------|----------|
| 0 | None (pure prompt) | Writing styles, reasoning patterns |
| 1 | File only | Scratchpad, planning, memory palace |
| 2 | File + execution | Code review, debugging |
| 3 | Full access | Git workflow, deployment |

**Principle:** Use the lowest tier possible.

---

## Available Skills

### Tier 1: File-Only (Essential)

| Skill | Description | Use When |
|-------|-------------|----------|
| **scratchpad** | Working memory for thinking out loud | You need to think through a problem |
| **planning** | Structured task decomposition and tracking | Multi-step tasks |
| **memory-palace** | Spatial organization of knowledge | Building knowledge bases |
| **adventure-protocol** | Room-based exploration with narrative | Exploring unfamiliar codebases |

### Tier 2: Read + Execute

| Skill | Description | Use When |
|-------|-------------|----------|
| **code-review** | Systematic code analysis with evidence | Reviewing PRs, auditing code |

### Templates

| Skill | Description |
|-------|-------------|
| **basic-skill** | Minimal template for creating new skills |

---

## Skills in This Directory

| Path | Description |
|------|-------------|
| `INDEX.yml` | Skill registry — list of all skills |
| `skill-instantiation-protocol.md` | SIP: How skills are invoked |
| `delegation-object-protocol.md` | DOP: Self-like inheritance |
| `scratchpad/` | Working memory skill |
| `planning/` | Task management skill |
| `memory-palace/` | Spatial knowledge organization |
| `adventure-protocol/` | Narrative exploration skill |
| `code-review/` | Code review skill |
| `templates/` | Skill templates for bootstrapping |

---

## Skill Anatomy

A skill is a directory:

```
skills/
  my-skill/
    SKILL.md           # Human-readable description
    PROTOTYPE.yml      # Machine-readable definition
    template/          # Files to copy on instantiation
      TASK.yml.tmpl    # Template with placeholders
      CHECKLIST.md     # Steps to follow
      working_set.yml  # Initial context
    examples/          # Usage examples (optional)
```

---

## Key Principles

### 1. Skills are Documents
A skill is defined by its documentation, not its code.
The model reads the docs and follows them.

### 2. Skills are Instantiated
Running a skill = copying its template into a session workspace.
The instance is the activation record.

### 3. Skills can Compose
Skills can delegate to other skills via prototype chains.
Self-like inheritance through file lookup.

### 4. Skills are Debuggable
Every skill action is visible in files.
No hidden state, no magic.

---

## Quick Start

### Use a Skill

1. Read the skill's `SKILL.md` to understand it
2. Copy the `template/` files to your working directory
3. Fill in the templates with your specifics
4. Follow the documented protocol

### Create a New Skill

1. Create directory: `skills/my-skill/`
2. Write `SKILL.md` describing the protocol
3. Write `PROTOTYPE.yml` with definition
4. Create `template/` with starter files
5. Register in `INDEX.yml`

See `templates/basic-skill/` for a minimal example.

---

## Integration with MOOLLM

Skills connect to MOOLLM protocols:

| Skill Concept | MOOLLM Equivalent |
|---------------|-------------------|
| Skill prototype | Trading card template |
| Skill instance | Room activation |
| Template files | Character soul structure |
| Checklist | Protocol steps |
| Delegation | Pet inheritance |

---

**See also:**
- `INDEX.yml` — Full skill registry
- `../kernel/` — Low-level protocols
- `../MOOLLM-PROTOCOLS.md` — Protocol compendium
- `../schemas/` — Data formats
