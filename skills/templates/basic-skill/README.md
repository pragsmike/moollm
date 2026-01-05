# 🧩 Basic Skill Template

> Minimal starter template for creating new MOOLLM skills

Copy this directory to create a new skill.

**Quick Links:**
- [Full Specification](SKILL.md) — protocol template
- [Template: TASK.yml](TASK.yml.tmpl) — task definition
- [Template: CHECKLIST.md](CHECKLIST.md.tmpl) — task checklist
- [Template: working_set.yml](working_set.yml.tmpl) — working set

## Usage

```bash
cp -r skills/templates/basic-skill skills/my-new-skill
```

Then:
1. Edit `SKILL.md` with your YAML frontmatter and protocol
2. Edit `README.md` (this file, but for your skill)
3. Edit `*.tmpl` files for instance creation
4. Register in [INDEX.yml](../../INDEX.yml)

## Related

- [templates/](../) — parent template directory
- [play-learn-lift](../../play-learn-lift/) — LIFT stage creates new skills
