# Potential Upstream Pull Requests

This document tracks changes in the local repository that are candidates for upstreaming to `SimHacker/moollm`.

## 1. Antigravity Driver Support
**Goal:** Enable native support for Google DeepMind's Antigravity agent (Tier 5).

### Included Files
-   **[NEW]** `kernel/drivers/antigravity.yml`
    -   Defines the Tier 5 driver, mapping `view_file`, `browser_subagent`, etc.
-   **[MODIFY]** `skills/bootstrap/SKILL.md`
    -   Updates detection logic to recognize "Antigravity" in system prompts and presence of Tier 5 tools.
-   **[MODIFY]** `kernel/drivers/README.md`
    -   adds `antigravity.yml` to the driver registry.

### Status
✅ **Ready.** Implemented and verified via manual probe.

---

## 2. Probe Documentation Fix
**Goal:** Align documentation with `MOOLLM.yml` configuration regarding the location of the bootstrap probe file.

### included Files
-   **[MODIFY]** `skills/bootstrap/SKILL.md`
    -   Corrected output location from "workspace root" to `.moollm/bootstrap-probe.yml`.
-   **[MODIFY]** `skills/bootstrap/README.md`
    -   Corrected output location to match config.

### Context
`MOOLLM.yml` defines `probe: .moollm/bootstrap-probe.yml`. The upstream documentation incorrectly stated it was at the root, causing confusion and `.gitignore` conflicts.

### Status
✅ **Ready.** Documentation now matches reality.

---

## 3. Adversarial Committee: Smart Selection (Draft)
**Goal:** Implement `FORM-SMART` logic for dynamic, diversity-based committee formation.

### Included Files
-   **[NEW]** `skills/adversarial-committee/SELECTION.md`
    -   Defines the selection algorithm, diversity scoring (Propensity, Risk, Epistemology), and character pool requirements.
-   **[MODIFY]** `skills/adversarial-committee/SKILL.md`
    -   Integrates `FORM-SMART` as a valid formation strategy.
-   **[MODIFY]** `skills/adversarial-committee/README.md`
    -   Adds documentation and examples for Smart Selection.

### Status
⚠️ **Draft / Needs Verification.**
-   Logic merged from local `mg` branch.
-   **Action Item:** Verify that the `FORM-SMART` logic actually works when invoked before finalizing this PR.

---

## 4. Repo Manifest Fix
**Goal:** Correct the upstream repository reference in `MOOLLM.yml`.

### Included Files
-   **[MODIFY]** `MOOLLM.yml`
    -   Updates `repo.github` from `leela-ai/moollm` to `SimHacker/moollm`.

### Status
✅ **Ready.** Simple configuration fix.
