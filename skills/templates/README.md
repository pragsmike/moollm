# 📦 Skill Templates

> How to create new MOOLLM skills

Start here when building a new skill from scratch.

## What's Here

```
templates/
└── basic-skill/          # Starter template
    ├── README.md         # Human-friendly landing page
    ├── SKILL.md          # Full spec with YAML frontmatter
    └── *.tmpl            # Templates at root level
```

## Creating a New Skill

### 1. Copy the Template

```bash
cp -r skills/templates/basic-skill skills/my-new-skill
```

### 2. Edit Files

| File | What to Change |
|------|----------------|
| `SKILL.md` | YAML frontmatter + full documentation |
| `README.md` | Human-friendly overview |
| `*.tmpl` | Instance file templates |

### 3. Register in INDEX.yml

Add to `skills/INDEX.yml`:

```yaml
- name: "my-new-skill"
  path: "skills/my-new-skill"
  description: "What it does"
  tier: 2
```

## New Skill Structure

Every skill follows this pattern:

```
skill-name/
├── README.md         # Human landing page (GitHub renders this)
├── SKILL.md          # Full spec with YAML frontmatter
└── *.tmpl            # Templates at root (not in template/)
```

## YAML Frontmatter

```yaml
---
name: my-skill
description: "One-line summary"
tier: 1
allowed-tools:
  - read_file
  - write_file
templates:
  - TASK.yml.tmpl
---
```

## Capability Tiers

| Tier | Needs | Examples |
|------|-------|----------|
| 0 | Nothing (knowledge only) | Guidelines |
| 1 | File read/write | Memory palace, planning |
| 2 | + Terminal | Debugging, builds |

## Navigation

| Direction | Destination |
|-----------|-------------|
| ⬆️ Up | [skills/](../) |
| 📋 Registry | [INDEX.yml](../INDEX.yml) |

*Start simple. Let the skill grow through use.*
