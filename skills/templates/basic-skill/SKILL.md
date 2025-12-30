# Basic Skill Template

## Purpose

A minimal skill template demonstrating SIP structure.
Use this as a starting point for creating new skills.

## When to Use

- Learning how skills work
- Creating a simple, single-purpose skill
- Bootstrapping a new skill

## Prerequisites

- File tools (fs.read, fs.write, fs.ls)
- No external dependencies

## Protocol

### Step 1: Understand the Task

1. Read TASK.yml to understand what needs to be done
2. Review any attached context files
3. Clarify ambiguities before proceeding

### Step 2: Execute

1. Follow the specific task instructions
2. Document progress in state/progress.yml
3. Create artifacts in artifacts/

### Step 3: Finalize

1. Write RESULT.md summarizing what was done
2. Write RETURN.md with compact output
3. Update INSTANCE.yml status to "finalized"

## Inputs

- **TASK.yml**: Task specification
  - `name`: What to call this task
  - `description`: What needs to be done
  - `parameters`: Task-specific parameters

## Outputs

- **RESULT.md**: Full description of what was accomplished
- **RETURN.md**: Compact output for parent context
- **artifacts/**: Any generated files

## Examples

See `examples/` directory:
- `simple/`: Basic usage
- `with-artifacts/`: Generating output files

## Tips

1. Always read TASK.yml first
2. Update progress as you go
3. Write RESULT.md even on failure
4. Keep RETURN.md under 200 words
