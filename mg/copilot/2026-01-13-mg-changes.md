# 📋 Changes & Decisions Summary

This document summarizes key changes made to `mg/` and decisions that affect how to continue working with this directory.

---

## 🎯 Major Changes Since Initial README

### 1. **Debate Propensities Added to All Characters** ⭐ CRITICAL

**What Changed:**
- All character files now include explicit `propensity` sections
- Each character has: type, risk_tolerance, epistemology, surfaces, voice, debate_role

**Why It Matters:**
- Propensities are **essential** for effective adversarial committee debates
- Without propensities, characters may agree too quickly or miss blind spots
- Propensities force incompatible values, creating genuine debate

**What You Need to Know:**
- When creating new characters, **always include propensities**
- See `characters/README.md` for the propensity structure
- Use `CHARACTER-RUBRIC.md` to evaluate if propensities are well-defined
- Different propensities = better debates (diversity is key)

**Files Affected:**
- All 18 character files in `characters/`
- `characters/README.md` (updated with propensity documentation)

---

### 2. **Character Evaluation System Created**

**What Changed:**
- Created `CHARACTER-RUBRIC.md` (25 criteria, 0-100 point scoring system)
- Created `CHARACTER-SCORES.md` (scores for all 18 characters)
- All characters scored: 4 Excellent (80-84), 11 Strong (70-79), 2 Adequate (60-69)

**Why It Matters:**
- Provides objective way to assess character quality for debates
- Identifies which characters need improvement
- Helps ensure team composition is balanced

**What You Need to Know:**
- Use the rubric when creating new characters
- Aim for 75+ points for strong debate participants
- Check `CHARACTER-SCORES.md` to see what works well
- Team composition matters — diverse propensities score better

**Files Created:**
- `CHARACTER-RUBRIC.md`
- `CHARACTER-SCORES.md`

---

### 3. **MOOLLM Behaviors Guide Created**

**What Changed:**
- Created `BEHAVIORS.md` with comprehensive guide to MOOLLM behaviors
- Documents DEBATE, ADVERSARIAL-COMMITTEE, ROBERTS-RULES, SOUL-CHAT, etc.
- Explains how to invoke behaviors via K-Lines or file structure

**Why It Matters:**
- Shows what tools are available for scenarios
- Explains when to use which behavior
- Helps design better scenarios

**What You Need to Know:**
- Read `BEHAVIORS.md` before designing scenarios
- Mention protocol names (e.g., `DEBATE`) to invoke behaviors
- Structure your `SCENARIO.yml` to align with behavior expectations

**Files Created:**
- `BEHAVIORS.md`

---

### 4. **Company/Person Name Aliasing System**

**What Changed:**
- All real company names replaced with fictional aliases
- All real person names replaced with fictional aliases
- Created private alias mapping files (excluded from git)

**Why It Matters:**
- Legal protection — avoids trademark/copyright issues
- Safe for public distribution
- Maintains recognizability for industry insiders

**What You Need to Know:**
- **Never commit** `.company-aliases.yml` or `.person-aliases.yml` (in `.gitignore`)
- When adding new characters, use aliases for any real companies/people mentioned
- Product vendors (Avid, Dolby, Genelec, SSL, Backblaze) are OK to keep as-is
- See alias files for mappings (but don't make them public)

**Files Created:**
- `.company-aliases.yml` (private)
- `.person-aliases.yml` (private)
- `.gitignore` (protects alias files)

**Files Updated:**
- All character files and bios (15 companies, 3 people aliased)

---

### 5. **Scenario Structure Clarified**

**What Changed:**
- Root `SCENARIO.yml` is now a template/legacy file
- New scenarios should use `scenarios/.template-SCENARIO.yml`
- Each scenario gets its own directory with its own `SCENARIO.yml`

**Why It Matters:**
- Clearer structure for multiple scenarios
- Each scenario is self-contained
- Easier to manage scenario-specific state

**What You Need to Know:**
- Create new scenarios in `scenarios/[scenario-name]/`
- Copy `scenarios/.template-SCENARIO.yml` (not root `SCENARIO.yml`)
- Each scenario has its own state, participants, topic

**Files:**
- `scenarios/.template-SCENARIO.yml` (template)
- `mg/SCENARIO.yml` (legacy/template, kept for reference)

---

## 🎯 Key Decisions Made

### Decision 1: Propensities Are Required
**Decision:** All characters must have explicit propensities for effective debates.

**Rationale:** Without propensities, characters lack clear debate roles and may not challenge effectively.

**Implication:** When creating new characters, always include propensity section. Use `CHARACTER-RUBRIC.md` to verify quality.

---

### Decision 2: Use Aliases for Real Entities
**Decision:** Replace real company/person names with fictional aliases in character bios.

**Rationale:** Legal protection and safe public distribution.

**Implication:** Always use aliases when mentioning real companies/people. Keep alias files private.

---

### Decision 3: Character Evaluation System
**Decision:** Use rubric-based scoring (0-100 points) to evaluate character quality.

**Rationale:** Objective assessment helps ensure debate effectiveness.

**Implication:** Score new characters using the rubric. Aim for 75+ points. Check existing scores for reference.

---

### Decision 4: Scenario-Specific State Files
**Decision:** Each scenario has its own `SCENARIO.yml` in its own directory.

**Rationale:** Multiple scenarios can run independently with different participants and topics.

**Implication:** Create scenarios in `scenarios/` subdirectories. Use template file.

---

## 📚 What Someone Needs to Know to Continue

### Essential Knowledge

1. **Propensities are mandatory** — Every character needs explicit propensities
2. **Use the rubric** — Evaluate characters before using them in debates
3. **Aliases are required** — Use fictional names for real companies/people
4. **Scenarios are self-contained** — Each in its own directory with its own state file
5. **Behaviors are available** — See `BEHAVIORS.md` for what you can use

### Workflow for New Characters

1. Write bio in `bios/` (use aliases for real entities)
2. Transform to character file (include propensities)
3. Score using `CHARACTER-RUBRIC.md`
4. If score < 75, improve character (add weaknesses, strengthen voice, etc.)
5. Add to appropriate scenarios

### Workflow for New Scenarios

1. Create `scenarios/[scenario-name]/` directory
2. Copy `scenarios/.template-SCENARIO.yml` to `scenarios/[scenario-name]/SCENARIO.yml`
3. Set active participants (character file paths)
4. Set topic, type, and protocol (e.g., `DEBATE`)
5. Create `README.md` describing the scenario
6. Optionally update `SCENARIOS.yml` to register it

### Important Files to Reference

- `characters/README.md` — Character format and propensities
- `CHARACTER-RUBRIC.md` — How to score characters
- `CHARACTER-SCORES.md` — Current character scores (reference)
- `BEHAVIORS.md` — Available MOOLLM behaviors
- `scenarios/README.md` — How to create scenarios
- `scenarios/.template-SCENARIO.yml` — Template for new scenarios

---

## ⚠️ Common Pitfalls to Avoid

1. **Forgetting propensities** — Characters without propensities won't debate effectively
2. **Using real company names** — Always use aliases (check `.company-aliases.yml`)
3. **Using real person names** — Always use aliases (check `.person-aliases.yml`)
4. **Committing alias files** — They're in `.gitignore` for a reason
5. **Creating scenarios in wrong place** — Use `scenarios/` subdirectories, not root
6. **Not evaluating characters** — Use the rubric to ensure quality

---

## 🎯 Next Steps for Continuation

1. **Create scenarios** — Use existing characters in debate scenarios
2. **Test debates** — Run scenarios and see how propensities work in practice
3. **Calibrate** — Adjust propensities if debates are too conflict-heavy or too consensus-driven
4. **Add more characters** — Follow the workflow and ensure propensities
5. **Document patterns** — Note what works well in actual debates

---

*This summary reflects the state of `mg/` after initial setup and character development.*

