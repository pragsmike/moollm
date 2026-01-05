# Mike Gallaher's Contributions to MOOLLM

> *"Everything is a story. Math proofs are stories. Legal theories are stories. Decision trees, causal analysis, risk assessments—all stories."*

## Origin

**Date:** January 5, 2026  
**From:** Mike Gallaher (pragsmike@gmail.com)  
**To:** Don Hopkins (don@donhopkins.com)  
**Subject:** Stories all the way down

## Background

Mike Gallaher and Don Hopkins have been friends and collaborators since their work together on:

- **UniPress Emacs** (which RMS calls "Software Hoarder Emacs")
- **NeMACS** — the NeWS version of Emacs
- **Pie Menus** — collaboratively conceived over bong hits after Mike's wedding to Liz Sommers

---

## The Core Insight: Stories All the Way Down

LLMs are essentially **storytelling machines**. To get them to be useful, cast inquiries in terms of stories.

This works because:
- Stories are how brains survive in fiendishly complex worlds
- For problems without obvious correct answers (most of them), stories game out possibilities
- **Mechanism fails to comprehend complex systems** — but stories capture enough structure to be useful

### Stories as Charts on a Manifold

You can't capture a sphere with a single flat map. You need multiple overlapping projections.

> Maya's paranoid realism reveals political dynamics that Joe's continuity-guardian view misses. Frankie's idealism surfaces value conflicts that Vic's evidence-prosecutor frame treats as out-of-scope. Tammy's systems view catches feedback loops everyone else ignores.

**No single story is "true" — but the ensemble approximates actionable wisdom.**

Technical term: **ensemble inference over the latent space of possible framings**.

---

## Mike's Committee Methodology

Mike has been using LLMs for examining tradeoffs and making decisions under uncertainty through:
- Diverse personas and patterns
- Adversarial debate committees
- Scoring by rubric
- Independent critics
- Story generation across different situations

### The Committee

A fixed roster of characters with specific propensities:

| Character | Propensity | Role |
|-----------|------------|------|
| **Maya** | Paranoid realism | Surfaces political dynamics |
| **Frankie** | Idealism | Reveals value conflicts |
| **Joe** | Continuity guardian | Protects institutional memory |
| **Vic** | Evidence prosecutor | Demands proof |
| **Tammy** | Systems thinker | Catches feedback loops |

### The Process

1. **Committee Formation** — Fixed roster with opposing propensities
2. **Robert's Rules** — Parliamentary procedure prevents short-circuiting
3. **Independent Evaluation** — Separate model scores against RUBRIC
4. **RUBRIC-Based Scoring** — Qualitative debate → quantitative decisions
5. **Cross-Scenario Learning** — Institutional memory across cycles

---

## Mapping to MOOLLM

Mike's patterns map directly onto MOOLLM infrastructure:

### ADVERSARIAL-COMMITTEE → Cards in Deliberation Room

```yaml
committee:
  cards:
    - maya:
        propensity: paranoid_realism
        risk_tolerance: low
        epistemology: assume_bad_faith
    - frankie:
        propensity: idealism
        risk_tolerance: high
        epistemology: assume_good_faith
    - joe:
        propensity: continuity
        risk_tolerance: medium
        epistemology: trust_precedent
    - vic:
        propensity: evidence_demanding
        risk_tolerance: medium
        epistemology: prove_it
    - tammy:
        propensity: systems_thinking
        risk_tolerance: varies
        epistemology: trace_feedback_loops
        
  simulation: SPEED-OF-LIGHT
  protocol: ROBERTS-RULES
```

### ROBERTS-RULES → Protocol Enforcing Staged Progression

```yaml
procedure:
  stages:
    - call_to_order
    - review_minutes      # What did we decide last time?
    - new_business
    - motion              # Someone proposes
    - second              # Someone supports
    - debate              # Structured argument
    - vote                # Recorded decision
    - adjourn
    
  rules:
    - each_stage_must_complete
    - no_skipping_to_conclusion
    - minority_views_recorded
```

### INDEPENDENT-EVALUATOR → Separate Room, No Context

```yaml
evaluation:
  pattern: |
    Committee output → THROW → evaluation-room/inbox/
    Evaluator has NO debate context
    Score against RUBRIC
    If score fails: critique → THROW → committee-room/inbox/
    Loop until pass or max_iterations
    
  why: |
    Prevents committee from gaming their own metrics.
    They can't see what the evaluator is thinking.
```

### RUBRIC-BRIDGE → Advertisement Scoring

```yaml
rubric:
  criteria:
    - resource_efficiency: weight: 0.2
    - risk_level: weight: 0.3
    - strategic_alignment: weight: 0.25
    - stakeholder_impact: weight: 0.25
    
  scoring:
    each_option_advertises_scores: true
    committee_debates_accuracy: true
    rubric_determines_priority: true
```

### CROSS-SCENARIO-LEARNING → Working Set Assembly

```yaml
learning:
  pattern: |
    Tag decisions: @decision @topic @outcome
    Future deliberations assemble working_set from:
      - Related past decisions
      - Outcomes of similar choices
      - Lessons learned
      
  files:
    - decisions/2026-01-05-client-choice.yml
    - decisions/2025-12-15-pricing-strategy.yml
    - lessons/client-scope-creep.md
```

### COPILOT-STATE-CAPTURE → Already the Default!

```yaml
persistence:
  pattern: FILES-AS-STATE
  everything_in_filesystem: true
  
  directories:
    - committee/roster.yml
    - committee/rubrics/
    - committee/decisions/
    - committee/minutes/
```

---

## The Critical Insight: Why Adversarial Storytelling Works

LLMs are correlation engines trained on text that encodes:
- Centuries of conflated causation with correlation
- Post-hoc rationalization as causal explanation
- Survivorship bias
- Genre conventions privileging certain narratives

A single confident answer gives you:
1. The statistical center of gravity of what "sounds right"
2. Hidden assumptions about stakeholders, success, constraints
3. Genre conventions
4. Survivorship bias from training corpus

**Adversarial storytelling performs structured perturbation of the narrative space:**

- One story assumes good faith; another bad faith; a third incompetence
- One optimizes for revenue; another sustainability; a third learning
- One emphasizes first-order effects; another traces feedback loops

Stories surviving cross-examination from multiple perspectives are more likely **robust to hidden assumptions**.

---

## The Danger: Mistaking Story for Reality

The AI will confidently tell a story that:
- Sounds coherent
- Fits genre conventions
- Feels predictive
- Is actually high-entropy bullshit that happens to be locally plausible

**The map is not the territory. The story is not the reality.**

Defense (same as humans use in high-stakes domains):
- **Adversarial review** — make stories fight each other
- **Demand for evidence** — what would prove this story wrong?
- **Testable predictions** — what does this story predict that's verifiable?
- **Epistemic humility** — acknowledge uncertainty

---

## Why AI is Weirdly Good at Sociotechnical Analysis

Despite no lived experience, LLMs can be surprisingly insightful about:
- Organizational dynamics
- Interpersonal conflict
- Strategic decisions

Not because AI understands human psychology deeply — but because it has pattern-matched over **the corpus of stories humans tell**:
- Case studies and postmortems
- Management books and advice columns
- Therapy transcripts and depositions
- Novels and memoirs
- All the places where people eventually speak bluntly

The AI samples from the genre of **"stories people tell when the polite fictions have dropped away."**

---

## The Game Within the Game

You can't eliminate uncertainty. You can't make AI always right.

But you can **play a better game**:

- Not naive trust (AI is always right)
- Not hypervigilance (it's trying to trick you)
- But treating it as a **narrative engine exploring possibility space faster than you could alone**

Build a game within the game where:
- Generate more candidate stories than solo
- Stress-test harder than confirmation bias allows
- Catch bad assumptions before acting
- Maintain appropriate skepticism without paranoia
- Distribute cognitive load

> "The AI isn't your enemy. But it's not your friend either. It's a stochastic parrot that sometimes says useful things."
>
> "The universe isn't hostile. But it's not benevolent either. It's vast, indifferent, and entropic."

---

## Practical Prompting Strategy

**Instead of:** "What should I do about this client situation?"

**Try:** "Tell me three different stories from incompatible perspectives. One assumes good faith, one bad faith, one incompetence. What does each predict? What evidence would distinguish them?"

---

**Instead of:** "Is this a good business decision?"

**Try:** "Maya thinks this is a trap. Frankie thinks it's an opportunity we'll regret missing. Joe thinks we should wait. Vic wants financials. Tammy thinks the real question is stakeholder relationships. Have them debate."

---

## Conclusion

> "The question is never 'which story is true?' The question is: 'Which story is useful for the decision I'm facing, given what I value and what I'm willing to risk?'"

LLMs let you generate and stress-test stories faster. But they don't tell you which story to live by.

**That part is still yours.**

---

## Skills Derived from This Work

These MOOLLM skills implement Mike's methodology:

| Skill | Purpose |
|-------|---------|
| [adversarial-committee/](../skills/adversarial-committee/) | Committee formation and structured debate |
| [roberts-rules/](../skills/roberts-rules/) | Parliamentary procedure protocol |
| [rubric/](../skills/rubric/) | Scoring against measurable criteria |
| [evaluator/](../skills/evaluator/) | Independent evaluation without context |

---

## Credits

**Mike Gallaher** — Core methodology, committee patterns, "Stories All the Way Down" essay, Robert's Rules adaptation, rubric-based evaluation, adversarial storytelling framework.

**Don Hopkins** — MOOLLM infrastructure, YAML Jazz, Speed of Light simulation, Pie Menus (co-invented with Mike over bong hits after Mike's wedding to Liz Sommers).

---

*"For everyone navigating complexity with imperfect tools, building things that matter, and trying not to mistake the map for the territory."*
