# Planning Skill
## Structured Task Decomposition and Progress Tracking

*"A plan is a hypothesis. Execution is the experiment."*

---

## Purpose

Manage complex tasks through:
- Structured decomposition into steps
- Persistent progress tracking
- Revision history
- Clear success criteria

This is the foundational skill for any multi-step work.

---

## When to Use

- Any task requiring multiple steps
- When you need to pause and resume
- Collaborative tasks needing handoff
- Complex debugging or investigation
- Project milestones

---

## Prerequisites

- File tools (read, write)
- Tier 1 (no execution)

---

## Protocol

### Step 1: Create the Plan

1. State the objective clearly
2. Define success criteria
3. Decompose into ordered steps
4. Identify dependencies
5. Write PLAN.yml

### Step 2: Execute

For each step:
1. Mark as `in_progress`
2. Do the work
3. Record outcome
4. Mark as `done` or `blocked`
5. Proceed or revise

### Step 3: Adapt

As you learn:
- Add discovered steps
- Remove unnecessary steps
- Reorder based on new information
- Note why changes were made

### Step 4: Complete

1. Verify all criteria met
2. Mark plan complete
3. Write retrospective notes
4. Archive or reference

---

## Core Files

### PLAN.yml
```yaml
plan:
  name: "Add User Authentication"
  objective: "Implement secure login/logout for the web app"
  status: "in_progress"
  created: "2025-12-30"
  
success_criteria:
  - "Users can register with email/password"
  - "Users can log in and receive session token"
  - "Protected routes reject unauthenticated requests"
  - "Users can log out"

steps:
  - id: 1
    name: "Set up auth database schema"
    status: "done"
    outcome: "Created users table with password hash column"
    
  - id: 2
    name: "Implement password hashing"
    status: "done"
    outcome: "Using bcrypt with cost factor 12"
    
  - id: 3
    name: "Create registration endpoint"
    status: "in_progress"
    notes: "Working on validation"
    depends_on: [1, 2]
    
  - id: 4
    name: "Create login endpoint"
    status: "pending"
    depends_on: [2, 3]
    
  - id: 5
    name: "Implement session tokens"
    status: "pending"
    depends_on: [4]
    
  - id: 6
    name: "Add auth middleware"
    status: "pending"
    depends_on: [5]
    
  - id: 7
    name: "Create logout endpoint"
    status: "pending"
    depends_on: [5]

blockers: []

revisions:
  - date: "2025-12-30T14:00"
    change: "Added step 5 - realized we need explicit session tokens"
    reason: "JWT alone isn't sufficient for logout"

notes: |
  Using session tokens in Redis for ability to invalidate.
  Consider adding refresh tokens in future iteration.
```

### PROGRESS.md
```markdown
# Progress: Add User Authentication

## Objective
Implement secure login/logout for the web app.

---

## Status: IN PROGRESS (3/7 steps)

### ✅ Completed
1. [x] Set up auth database schema
   - Created users table with password hash column
   
2. [x] Implement password hashing
   - Using bcrypt with cost factor 12

### 🔄 In Progress
3. [ ] Create registration endpoint
   - Working on validation
   - Need to handle duplicate emails

### ⏳ Pending
4. [ ] Create login endpoint
5. [ ] Implement session tokens
6. [ ] Add auth middleware
7. [ ] Create logout endpoint

---

## Blockers
*None currently*

---

## Notes
- Using session tokens in Redis for invalidation
- Consider refresh tokens later

---

## Timeline
- Started: 2025-12-30
- Est. Completion: 2025-12-31
```

---

## Step States

| State | Symbol | Meaning |
|-------|--------|---------|
| `pending` | ⏳ | Not yet started |
| `in_progress` | 🔄 | Currently working on |
| `done` | ✅ | Successfully completed |
| `blocked` | 🚫 | Cannot proceed |
| `skipped` | ⏭️ | Intentionally skipped |

---

## Commands

| Intent | Action |
|--------|--------|
| "Create plan" | Write PLAN.yml and PROGRESS.md |
| "Check status" | Read PLAN.yml status |
| "Start step N" | Mark step N as in_progress |
| "Complete step N" | Mark step N as done, record outcome |
| "Block on X" | Mark step blocked, add to blockers |
| "Add step" | Insert new step, note in revisions |
| "Review progress" | Read PROGRESS.md |
| "Complete plan" | Mark plan done, verify criteria |

---

## Dependencies

Steps can declare dependencies:
```yaml
- id: 4
  name: "Create login endpoint"
  depends_on: [2, 3]
```

Rules:
- Cannot start a step until dependencies are `done`
- Circular dependencies are errors
- Dependencies should be explicit

---

## Revisions

Track plan changes:
```yaml
revisions:
  - date: "2025-12-30T14:00"
    change: "Added step 5"
    reason: "Discovered need for session tokens"
    
  - date: "2025-12-30T15:30"
    change: "Reordered steps 6 and 7"
    reason: "Middleware needed before logout"
```

---

## Tips

1. **Start with criteria** — Know what "done" means
2. **Small steps** — Easier to track and adjust
3. **Explicit dependencies** — Prevents parallel confusion
4. **Record outcomes** — Not just "done" but what happened
5. **Revise freely** — Plans should evolve
6. **Note blockers** — Don't hide impediments

---

## Outputs

- PLAN.yml with structured plan and progress
- PROGRESS.md with human-readable status
- Audit trail of revisions
- Transferable project state
