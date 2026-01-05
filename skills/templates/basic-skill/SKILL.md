---
name: basic-skill
description: Minimal starter template for creating new MOOLLM skills
license: MIT
tier: 1
allowed-tools:
  - read_file
  - write_file
templates:
  - TASK.yml.tmpl
  - CHECKLIST.md.tmpl
  - working_set.yml.tmpl
---

# Basic Skill Template

A minimal skill template demonstrating the new skill structure. Use this as a starting point for creating new skills.

## When to Use

- Learning how skills work
- Creating a simple, single-purpose skill
- Bootstrapping a new skill

## Protocol

### Step 1: Understand the Task

1. Read TASK.yml to understand what needs to be done
2. Review any attached context files
3. Clarify ambiguities before proceeding

### Step 2: Execute

1. Follow the specific task instructions
2. Document progress
3. Create artifacts as needed

### Step 3: Finalize

1. Write RESULT.md summarizing what was done
2. Write RETURN.md with compact output
3. Update status to "finalized"

## Inputs

- **TASK.yml**: Task specification
  - `name`: What to call this task
  - `description`: What needs to be done
  - `parameters`: Task-specific parameters

## Outputs

- **RESULT.md**: Full description of what was accomplished
- **RETURN.md**: Compact output for parent context
- **artifacts/**: Any generated files

## Tips

1. Always read TASK.yml first
2. Update progress as you go
3. Write RESULT.md even on failure
4. Keep RETURN.md under 200 words
