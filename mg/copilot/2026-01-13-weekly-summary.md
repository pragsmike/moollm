# 🗞️ Weekly Change Narrative (Jan 6 - Jan 13, 2026)

## The Tale of Two Directories

The past week has seen the repository bifurcate into two distinct streams of evolution: the **Stable Kernel** (preparing for upstream) and the **Experimental Sandbox** (`mg`), which is rapidly evolving a sophisticated character ontology.

---

### 1. The Sandbox (`mg/`) - "The Intelligence Explosion"
*Where we defined WHO the agents are and HOW they interact.*

The `mg` directory has transformed from a simple scratchpad into a rigorous testbed for agentic social dynamics.

*   **Character Ontology Revolution:** We moved beyond simple bios to a **Propensity-Based Model**. Every character now has explicit `risk_tolerance`, `epistemology`, and `debate_role`.
*   **The Rubric of Quality:** We introduced `CHARACTER-RUBRIC.md` (and the corresponding `CHARACTER-SCORES.md`), establishing an objective 0-100 scoring system to ensure characters are complex enough for adversarial debate.
*   **Behavior Codification:** `BEHAVIORS.md` was created to document the "unwritten rules" of the system (Debate, Roberts Rules, Soul Chat), turning folklore into protocol.
*   **Safety & Privacy:** We implemented a rigorous aliasing system (`.company-aliases.yml`) to sanitize real-world references, making the dataset safe for public release.
*   **Structure:** We moved from a monolithic `SCENARIO.yml` to a modular `scenarios/` directory structure.

### 2. The Upstream (`kernel/` & `skills/`) - "The Structural Foundation"
*Where we built the machinery for them to live in.*

While `mg` evolved the software (the minds), the root directories evolved the hardware (the drivers).

*   **Antigravity Driver (Tier 5):** We implemented native support for the Google Antigravity agent in `kernel/drivers/antigravity.yml`, granting it the necessary permissions ("Agent Gitignore Access").
*   **Bootstrap probe Fixes:** We corrected critical pathing errors in `skills/bootstrap` to match `MOOLLM.yml`.
*   **Smart Selection Logic:** We introduced the `FORM-SMART` logic in `skills/adversarial-committee`, allowing committees to self-assemble based on the very diversity metrics defined in `mg`.

---

## 🧹 Housekeeping Recommendations

To maintain this clarity, we should tidy up the artifacts:

1.  **Move `mg/CHANGES-SUMMARY.md` -> `mg/copilot/2026-01-13-mg-changes.md`**: This is a historical log of the "Sandbox Era" and belongs in the captain's log.
2.  **Move `mg/CHARACTER-RUBRIC.md` -> `mg/rubrics/character-rubric.md`**: We already have a `rubrics/` folder (containing `editorial-rubric.yml`). All scoring criteria should live together.
