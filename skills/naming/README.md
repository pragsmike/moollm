# 📛 Naming

> Big-endian file naming as semantic binding.

**Quick Links:**
- [Full Specification](SKILL.md) — complete protocol
- [Kernel: NAMING.yml](../../kernel/NAMING.yml) — definitive reference

## Overview

Files are named big-endian: `TYPE-VARIANT.ext`, e.g. `cat-terpie.yml`. The filesystem becomes a semantic network. Sorting reveals hierarchy.

## The Pattern

```
TYPE-VARIANT.ext
│    │
│    └── Specific instance
└────── Category/role

cat-terpie.yml      # A cat named Terpie
cat-stroopwafel.yml # Another cat
staff-marieke.yml   # Staff member
ROOM.yml            # Room definition (type only, no variant)
```

## Why Big-Endian?

- `ls` sorts by category first
- Easy to find "all cats" → `cat-*.yml`
- Clear inheritance hierarchy
- Inspired by Minsky's K-lines

## Related Skills

- [room/](../room/) — uses naming for organization
- [character/](../character/) — character naming patterns
- [yaml-jazz/](../yaml-jazz/) — names carry meaning
