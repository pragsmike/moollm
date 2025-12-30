# Scratchpad Skill
## Working Memory for Thinking Out Loud

*"Think on paper. The file is your extended mind."*

---

## Purpose

Provide persistent working memory through:
- A scratch file for ephemeral thinking
- Structured sections for different thought types
- Append-only operation for thought preservation
- Easy cleanup and archival

The simplest and most essential skill — just a place to think.

---

## When to Use

- Working through a complex problem
- Debugging with hypotheses
- Brainstorming ideas
- Keeping notes during exploration
- Any time you need to "think out loud"

---

## Prerequisites

- File tools (read, write/append)
- Tier 1 (no execution)

---

## Protocol

### Step 1: Open the Scratchpad

Create or read `scratch.md` in working directory.

### Step 2: Think Out Loud

Append thoughts as you work:
- Hypotheses and questions
- Observations and findings
- Decisions and rationale
- Temporary notes

### Step 3: Organize (Optional)

Use sections to categorize:
- `## Thinking` — Current reasoning
- `## Questions` — Open questions
- `## Findings` — What you've learned
- `## Decisions` — Choices made

### Step 4: Clean Up

When done:
- Extract valuable insights to permanent files
- Archive or delete the scratchpad
- Start fresh for next task

---

## Core File

### scratch.md
```markdown
# Scratchpad: [Task Name]
*Started: 2025-12-30T10:00*

---

## Thinking

Working through the authentication bug...

The error says "token expired" but the token was just created.
Hypothesis: Clock skew between services?

Let me check the token creation time... 
Created at 10:00:00, expires at 10:00:00 + 3600 = 11:00:00
Current time on auth service: 10:00:05
Current time on API service: ??? need to check

---

## Questions

- [ ] What's the time on the API server?
- [ ] Are they using NTP?
- [ ] Is there a grace period for token validation?

---

## Findings

1. Auth service uses UTC
2. API service config says UTC but... need to verify
3. Found similar issue in GitHub issues #234

---

## Decisions

- Will add 30-second grace period to token validation
- Reason: Clock skew is inevitable, grace period is standard practice

---

## Temporary Notes

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
Decoded: {"exp": 1735560000, "iat": 1735556400}
```

Config location: /etc/auth/config.yml

---

*Last updated: 2025-12-30T10:45*
```

---

## Sections

| Section | Purpose |
|---------|---------|
| `## Thinking` | Active reasoning, stream of consciousness |
| `## Questions` | Things to investigate |
| `## Findings` | Discovered facts |
| `## Decisions` | Choices with rationale |
| `## Temporary` | Snippets, references, junk |

---

## Commands

| Intent | Action |
|--------|--------|
| "Open scratchpad" | Create/read scratch.md |
| "Think about X" | Append to ## Thinking |
| "Question: X" | Add to ## Questions |
| "Found: X" | Add to ## Findings |
| "Decided: X" | Add to ## Decisions |
| "Note: X" | Add to ## Temporary |
| "Review thinking" | Read scratch.md |
| "Clear scratchpad" | Archive and start fresh |

---

## Append-Only Operation

The scratchpad should be **append-only** during a session:
- Never delete thoughts mid-session
- Strikethrough instead of delete: ~~wrong hypothesis~~
- This preserves the reasoning journey
- Clean up only at session end

```markdown
## Thinking

First thought: maybe it's a race condition?
~~Actually no, the logs show sequential execution~~
New thought: could be a caching issue instead
```

---

## Multiple Scratchpads

For complex work, use named scratchpads:
```
scratch-auth-bug.md
scratch-performance.md
scratch-refactor-ideas.md
```

Or use subdirectories:
```
scratch/
├── current.md      # Active thinking
├── auth-bug.md     # Specific investigation
└── archive/        # Old scratchpads
```

---

## Lifecycle

```
Create → Append → Append → ... → Extract → Archive/Delete
```

1. **Create** — Start fresh scratchpad
2. **Append** — Add thoughts as you work
3. **Extract** — Pull valuable insights to permanent files
4. **Archive** — Move to archive/ or delete

---

## Tips

1. **Don't edit, append** — Preserve your thinking journey
2. **Timestamp sections** — Helps track progression
3. **Be messy** — Scratchpads are for thinking, not presentation
4. **Extract insights** — Don't lose good ideas in scratch
5. **Fresh starts** — New task = new scratchpad
6. **Link context** — Reference files you're working with

---

## Outputs

- scratch.md with working notes
- Preserved reasoning journey
- Extracted insights (to other files)
- Clean mental workspace
