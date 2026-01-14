# 🗞️ Editorial Committee Process

> *"Trust, but Verify. Then Verify the Verification."*

The **Editorial Committee** is a specialized adversarial body that reviews the **Resolutions** produced by primary committees. Unlike the primary committee, the Editorial Committee treats the debate as a **Black Box**—it does not see the transcript, only the result.

## 🎯 Objective
To ensure that Resolutions are logically consistent, supported by evidence, and aligned with the Charter, *regardless* of how the consensus was reached. This prevents "charismatic but wrong" outcomes where a persuasive persona dominates the debate without substance.

---

## 🔒 The Black Box Protocol

The Editorial Committee operates under strict information isolation to ensure objectivity.

### inputs (What they SEE)
1.  **The Charter:** What was the problem? What were the success criteria? (`00-charter.yml`)
2.  **The Resolution:** What was decided? What is the rationale? (`03-resolution.yml`)
3.  **The Rubric:** The implementation-specific scoring criteria. (`rubric.yml`)
4.  **The Evidence:** (Optional) Raw documents referenced in the Resolution.

### excluded (What they DO NOT see)
1.  **The Transcript:** Who said what, the flow of debate, the emotional manipulation. (`02-deliberation.md`)
2.  **The Votes:** Who voted "Yes" or "No".
3.  **The Personas:** Which characters were on the primary committee.

---

## 👥 The Roster

The Editorial Committee is composed of specialized personas designed for scrutiny, not creation.

| Role | archetype | Responsibility | Propensity |
| :--- | :--- | :--- | :--- |
| **Editor-in-Chief** | *The Decider* | Overall coherence, alignment with Charter, brand voice. | `strategic_alignment` |
| **Fact Checker** | *The Investigator* | Verifies claims against provided evidence. Demands citations. | `verification_prosecutor` |
| **Logic Auditor** | *The Mathematician* | Checks internal consistency. Traces "If A, then B" logic chains. | `logical_rigor` |
| **Ombudsman** | *The Critic* | Represents the user/stakeholder perspective. Asks "So what?" | `stakeholder_advocacy` |

*Note: These are distinct from the primary committee members (Maya, Frankie, etc.).*

---

## 📝 The Process

### Phase 1: Intake
The Editor-in-Chief receives the `Resolution` and `Charter`. The Logic Auditor verifies that the Resolution actually addresses the questions posed in the Charter.

### Phase 2: Audit (Parallel Processing)
*   **Fact Checker:** Scans the Resolution for factual claims. "Is this true? Is it supported?"
*   **Logic Auditor:** Syllogism check. "Does the Rationale actually support the Decision?"
*   **Ombudsman:** Stakeholder check. "Does this create unhandled externalities?"

### Phase 3: Rubric Scoring
The committee applies the **Standard Editorial Rubric**:
1.  **Response to Charter:** Did they answer the question?
2.  **Internal Consistency:** Do the details contradict the summary?
3.  **Evidence Support:** Are claims substantial?
4.  **Feasibility:** Is the plan actionable?

### Phase 4: Critique Generation
The committee produces a **Critique Artifact** containing:
1.  **Score Analysis:** Breakdown by rubric criteria.
2.  **Blockers:** Fatal flaws that prevent publishing (Implementation).
3.  **Improvement Requests:** Specific questions sent back to the Primary Committee for clarification.

---

## 📤 Outputs

### 1. The Editorial Review (`04-editorial-review.yml`)
```yaml
review:
  status: "RETURNED_FOR_REVISION" | "APPROVED_FOR_PUBLICATION"
  scores:
    consistency: 3/5
    evidence: 2/5
    feasibility: 5/5
  
  critique:
    - "The resolution claims X, but the rationale describes Y."
    - "No evidence provided for the claim that 'users prefer Z'."
    
  requirements:
    - "Clarify the migration path for existing assets."
```

### 2. The Cycle
*   **If APPROVED:** The Resolution moves to Implementation.
*   **If RETURNED:** The Primary Committee reconvenes (with the Critique as new input) to amend the Resolution.
