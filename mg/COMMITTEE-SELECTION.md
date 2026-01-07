# 🎯 Committee Selection Guide

## Purpose

This guide helps you select characters from your pool to form committees that will:
- **Explore a wide swath of possibility space** (diverse perspectives)
- **Arrive at consensus without endless debate** (balanced composition)
- **Use ROBERTS-RULES when necessary** (structured deliberation)

---

## What MOOLLM Offers

MOOLLM provides the **ADVERSARIAL-COMMITTEE** protocol and **ROBERTS-RULES** procedure, but **committee selection is manual**. You choose members based on their propensities, then MOOLLM runs the debate.

### Key MOOLLM Components:

1. **ADVERSARIAL-COMMITTEE Protocol** (`skills/adversarial-committee/`)
   - Structures multi-perspective deliberation
   - Uses opposing propensities to force genuine debate
   - Integrates with ROBERTS-RULES for formal procedure

2. **ROBERTS-RULES Protocol** (`skills/roberts-rules/`)
   - Parliamentary procedure prevents premature consensus
   - Stages: Call to Order → Review Minutes → Motion → Second → Debate → Vote → Adjourn
   - Forces structured exploration of decision space

3. **SPEED-OF-LIGHT Simulation** (`skills/speed-of-light/`)
   - Runs entire committee debate within ONE LLM call
   - Natural flow without artificial turn-taking delays

---

## Selection Principles

### 1. **Diversity is Essential**

A good committee needs **opposing propensities** that create productive tension:

| Dimension | Why It Matters |
|-----------|----------------|
| **Propensity Type** | Different core perspectives (paranoid vs. idealist, operational vs. systems) |
| **Risk Tolerance** | Low/medium/high creates conflict over trade-offs |
| **Epistemology** | Different truth-finding methods (assume_bad_faith vs. assume_good_faith, prove_it vs. trust_precedent) |
| **Debate Role** | Different functions (devil's_advocate, opportunity_scout, historian, evidence_checker) |

### 2. **Balance for Consensus**

Too much diversity = endless debate. Too little = premature consensus.

**Ideal Committee Size:** 5-7 members
- **Minimum:** 3 members (too small, lacks diversity)
- **Maximum:** 9 members (too large, hard to reach consensus)

**Composition Guidelines:**
- **2-3 "pushers"** (low risk tolerance, paranoid, devil's advocate) — prevent rushing
- **1-2 "optimists"** (high risk tolerance, idealist, opportunity scout) — surface opportunities
- **1-2 "analysts"** (evidence-based, systems thinking) — provide grounding
- **1 "synthesizer"** (medium risk, can bridge perspectives) — help reach consensus

### 3. **Avoid Redundancy**

Don't include multiple characters with:
- Same propensity type
- Same epistemology
- Same debate role

**Exception:** If you need multiple perspectives on the same dimension (e.g., two evidence-checkers with different backgrounds), ensure they have different risk tolerances or other distinguishing factors.

---

## Character Pool Analysis

### By Propensity Type

| Propensity | Characters | Risk Tolerance | Epistemology | Debate Role |
|------------|------------|----------------|--------------|-------------|
| `paranoid_realism` | maya-tilted-hat | low | assume_bad_faith | devil's_advocate |
| `idealism` | frankie-kerouac | high | assume_good_faith | opportunity_scout |
| `continuity_guardian` | joe-gusher | medium | trust_precedent | historian |
| `evidence_prosecutor` | vic-eyebrow | medium | prove_it | evidence_checker |
| `systems_thinking` | tammy-silent | varies | trace_feedback_loops | systems_analyst |
| `operational_realism` | samir-patel | medium | prove_it | operational_reality_check |
| `evidence_guardian` | marcus-chen | medium | prove_it | evidence_guardian |
| `truth_teller` | elodie-vax | high | prove_it | truth_advocate |
| `reliability_engineer` | jamal-washington | low | prove_it | reliability_checker |
| `authenticity_seeker` | monica-rivers | medium | assume_good_faith | authenticity_advocate |
| `evidence_architect` | ravi-srinivasan | medium | prove_it | evaluation_architect |
| `compliance_guardian` | elena-morales | low | prove_it | compliance_checker |
| `opportunity_optimist` | derrick-ng | high | assume_good_faith | opportunity_scout |
| `pedagogical_experimenter` | jordan-kim | medium | assume_good_faith | learning_advocate |
| `delivery_realist` | patricia-oneal | medium | prove_it | delivery_reality_check |
| `cross_industry_innovator` | emma-nakamura | medium | assume_good_faith | innovation_scout |
| `creative_pragmatist` | sofia-ramirez | medium | assume_good_faith | creative_advocate |
| `curious_learner` | tyler-brooks | medium | assume_good_faith | learning_questioner |

### By Risk Tolerance

| Risk Tolerance | Characters |
|----------------|------------|
| **Low** | maya-tilted-hat, jamal-washington, elena-morales |
| **Medium** | Most characters (joe-gusher, vic-eyebrow, samir-patel, marcus-chen, monica-rivers, ravi-srinivasan, jordan-kim, patricia-oneal, emma-nakamura, sofia-ramirez, tyler-brooks) |
| **High** | frankie-kerouac, elodie-vax, derrick-ng |
| **Varies** | tammy-silent |

### By Epistemology

| Epistemology | Characters |
|--------------|------------|
| `assume_bad_faith` | maya-tilted-hat |
| `assume_good_faith` | frankie-kerouac, monica-rivers, derrick-ng, jordan-kim, emma-nakamura, sofia-ramirez, tyler-brooks |
| `trust_precedent` | joe-gusher |
| `prove_it` | vic-eyebrow, samir-patel, marcus-chen, elodie-vax, jamal-washington, ravi-srinivasan, elena-morales, patricia-oneal |
| `trace_feedback_loops` | tammy-silent |

### By Debate Role

| Debate Role | Characters |
|-------------|------------|
| `devil's_advocate` | maya-tilted-hat |
| `opportunity_scout` | frankie-kerouac, derrick-ng |
| `historian` | joe-gusher |
| `evidence_checker` | vic-eyebrow |
| `systems_analyst` | tammy-silent |
| `operational_reality_check` | samir-patel |
| `evidence_guardian` | marcus-chen |
| `truth_advocate` | elodie-vax |
| `reliability_checker` | jamal-washington |
| `authenticity_advocate` | monica-rivers |
| `evaluation_architect` | ravi-srinivasan |
| `compliance_checker` | elena-morales |
| `learning_advocate` | jordan-kim |
| `delivery_reality_check` | patricia-oneal |
| `innovation_scout` | emma-nakamura |
| `creative_advocate` | sofia-ramirez |
| `learning_questioner` | tyler-brooks |

---

## Selection Strategies

### Strategy 1: **Core Adversarial Committee** (5 members)

Based on Mike Gallaher's canonical committee pattern:

```yaml
committee:
  name: "Core Adversarial Committee"
  members:
    - maya-tilted-hat      # paranoid_realism, low risk, assume_bad_faith, devil's_advocate
    - frankie-kerouac      # idealism, high risk, assume_good_faith, opportunity_scout
    - joe-gusher           # continuity_guardian, medium risk, trust_precedent, historian
    - vic-eyebrow          # evidence_prosecutor, medium risk, prove_it, evidence_checker
    - tammy-silent         # systems_thinking, varies risk, trace_feedback_loops, systems_analyst
```

**Why This Works:**
- Maximum diversity: 5 different propensities, 3 different epistemologies, 5 different roles
- Balanced risk: low (Maya), high (Frankie), medium (Joe, Vic), varies (Tammy)
- Covers all bases: paranoia, idealism, precedent, evidence, systems

**Use When:** Need comprehensive exploration of a complex decision.

---

### Strategy 2: **Balanced Exploration** (6-7 members)

Add 1-2 more perspectives while maintaining balance:

```yaml
committee:
  name: "Balanced Exploration Committee"
  members:
    - maya-tilted-hat      # paranoid_realism, low risk, assume_bad_faith
    - frankie-kerouac      # idealism, high risk, assume_good_faith
    - joe-gusher           # continuity_guardian, medium risk, trust_precedent
    - vic-eyebrow          # evidence_prosecutor, medium risk, prove_it
    - tammy-silent         # systems_thinking, varies risk, trace_feedback_loops
    - samir-patel          # operational_realism, medium risk, prove_it (operational focus)
    - marcus-chen          # evidence_guardian, medium risk, prove_it (evaluation focus)
```

**Why This Works:**
- Adds operational and evaluation perspectives
- Still maintains diversity (7 different roles, 4 epistemologies)
- Multiple "prove_it" epistemologies but different roles (evidence_checker, operational_reality_check, evidence_guardian)

**Use When:** Need deeper operational and evaluation perspectives.

---

### Strategy 3: **Consensus-Focused** (5 members)

Optimized for reaching decisions without endless debate:

```yaml
committee:
  name: "Consensus-Focused Committee"
  members:
    - maya-tilted-hat      # paranoid_realism, low risk (pusher)
    - frankie-kerouac      # idealism, high risk (optimist)
    - joe-gusher           # continuity_guardian, medium risk (synthesizer)
    - tammy-silent         # systems_thinking, varies risk (analyst/synthesizer)
    - marcus-chen          # evidence_guardian, medium risk (analyst)
```

**Why This Works:**
- Fewer "prove_it" epistemologies (less evidence paralysis)
- Includes synthesizers (Joe, Tammy) who can bridge perspectives
- Still has tension (Maya vs. Frankie) but balanced with consensus-builders

**Use When:** Need to reach decisions efficiently while maintaining quality.

---

### Strategy 4: **Evidence-Heavy** (6 members)

For decisions requiring rigorous proof:

```yaml
committee:
  name: "Evidence-Heavy Committee"
  members:
    - maya-tilted-hat      # paranoid_realism, low risk, assume_bad_faith
    - vic-eyebrow          # evidence_prosecutor, medium risk, prove_it
    - marcus-chen          # evidence_guardian, medium risk, prove_it
    - ravi-srinivasan      # evidence_architect, medium risk, prove_it
    - tammy-silent         # systems_thinking, varies risk, trace_feedback_loops
    - joe-gusher           # continuity_guardian, medium risk, trust_precedent
```

**Why This Works:**
- Multiple evidence-focused roles (prosecutor, guardian, architect)
- Still includes paranoia (Maya) and systems thinking (Tammy)
- Precedent (Joe) provides historical context

**Use When:** Decisions require extensive evidence gathering and validation.

---

### Strategy 5: **Innovation-Focused** (6 members)

For exploring new opportunities:

```yaml
committee:
  name: "Innovation-Focused Committee"
  members:
    - frankie-kerouac      # idealism, high risk, assume_good_faith
    - derrick-ng           # opportunity_optimist, high risk, assume_good_faith
    - emma-nakamura        # cross_industry_innovator, medium risk, assume_good_faith
    - maya-tilted-hat      # paranoid_realism, low risk, assume_bad_faith (reality check)
    - tammy-silent         # systems_thinking, varies risk, trace_feedback_loops
    - vic-eyebrow          # evidence_prosecutor, medium risk, prove_it (evidence check)
```

**Why This Works:**
- Multiple optimists (Frankie, Derrick, Emma) explore opportunities
- Reality checks (Maya, Vic) prevent reckless decisions
- Systems thinking (Tammy) maps consequences

**Use When:** Exploring new opportunities, products, or markets.

---

## Selection Checklist

Before finalizing a committee, verify:

- [ ] **Diversity of propensities:** At least 4-5 different propensity types
- [ ] **Diversity of risk tolerance:** Mix of low, medium, and high
- [ ] **Diversity of epistemology:** At least 3 different epistemologies
- [ ] **Diversity of debate roles:** No duplicate roles (unless intentional)
- [ ] **Balance for consensus:** Include at least 1 synthesizer (medium risk, can bridge perspectives)
- [ ] **Appropriate size:** 5-7 members (3 minimum, 9 maximum)
- [ ] **Topic fit:** Members' backgrounds and expertise align with the decision topic

---

## Using ROBERTS-RULES

ROBERTS-RULES should be used when:

1. **Formal decisions are required** (budget approval, strategic direction)
2. **Stakeholders need documented process** (compliance, transparency)
3. **Committee is prone to premature consensus** (needs structured exploration)
4. **Multiple motions need to be considered** (complex decision space)

**How to Enable:**

```yaml
# In your SCENARIO.yml
scenario:
  protocol: ROBERTS-RULES
  committee:
    members: [...]
    chair: marcus-chen  # Designate a chair to run the meeting
```

**ROBERTS-RULES Stages:**
1. Call to Order
2. Review Minutes (if previous meeting)
3. New Business
4. Motion → Second → Debate → Vote
5. Adjourn

Each stage must complete before the next begins. This prevents jumping to conclusions.

---

## Committee Formation Template

```yaml
# scenarios/[scenario-name]/COMMITTEE.yml
committee:
  name: "Committee Name"
  purpose: "What they're deciding"
  
  members:
    - character: maya-tilted-hat
      role: devil's_advocate
      propensity: paranoid_realism
      risk_tolerance: low
      epistemology: assume_bad_faith
      
    - character: frankie-kerouac
      role: opportunity_scout
      propensity: idealism
      risk_tolerance: high
      epistemology: assume_good_faith
      
    # ... more members
    
  protocol: ROBERTS-RULES  # or DEBATE, ADVERSARIAL-COMMITTEE
  chair: marcus-chen  # Required if using ROBERTS-RULES
  
  evaluation:
    rubric: path/to/rubric.yml  # Optional: for independent evaluation
    evaluator: true  # Send output to independent evaluator
```

---

## Quick Reference: Character Selection Matrix

| Character | Propensity | Risk | Epistemology | Role | Best For |
|-----------|------------|------|--------------|------|----------|
| maya-tilted-hat | paranoid_realism | low | assume_bad_faith | devil's_advocate | Reality checks, uncovering hidden agendas |
| frankie-kerouac | idealism | high | assume_good_faith | opportunity_scout | Exploring opportunities, value conflicts |
| joe-gusher | continuity_guardian | medium | trust_precedent | historian | Institutional memory, precedent |
| vic-eyebrow | evidence_prosecutor | medium | prove_it | evidence_checker | Demanding proof, data gaps |
| tammy-silent | systems_thinking | varies | trace_feedback_loops | systems_analyst | Unintended consequences, feedback loops |
| samir-patel | operational_realism | medium | prove_it | operational_reality_check | Operational risks, 2 a.m. failures |
| marcus-chen | evidence_guardian | medium | prove_it | evidence_guardian | Evidence-based decisions, evaluation |
| elodie-vax | truth_teller | high | prove_it | truth_advocate | Uncomfortable truths, directness |
| jamal-washington | reliability_engineer | low | prove_it | reliability_checker | Reliability, failure modes |
| monica-rivers | authenticity_seeker | medium | assume_good_faith | authenticity_advocate | Authenticity, human values |
| ravi-srinivasan | evidence_architect | medium | prove_it | evaluation_architect | Evaluation frameworks, research |
| elena-morales | compliance_guardian | low | prove_it | compliance_checker | Regulatory, compliance |
| derrick-ng | opportunity_optimist | high | assume_good_faith | opportunity_scout | Optimism, opportunities |
| jordan-kim | pedagogical_experimenter | medium | assume_good_faith | learning_advocate | Learning, experimentation |
| patricia-oneal | delivery_realist | medium | prove_it | delivery_reality_check | Delivery, execution |
| emma-nakamura | cross_industry_innovator | medium | assume_good_faith | innovation_scout | Innovation, cross-industry |
| sofia-ramirez | creative_pragmatist | medium | assume_good_faith | creative_advocate | Creativity, pragmatism |
| tyler-brooks | curious_learner | medium | assume_good_faith | learning_questioner | Learning, questions |

---

## Next Steps

1. **Choose a selection strategy** based on your decision type
2. **Verify diversity** using the checklist
3. **Create COMMITTEE.yml** using the template
4. **Configure SCENARIO.yml** with protocol (ROBERTS-RULES if needed)
5. **Run the committee** using MOOLLM's ADVERSARIAL-COMMITTEE protocol

See also:
- [BEHAVIORS.md](./BEHAVIORS.md) — MOOLLM protocols and behaviors
- [CHARACTER-RUBRIC.md](./CHARACTER-RUBRIC.md) — Character evaluation criteria
- [CHARACTER-SCORES.md](./CHARACTER-SCORES.md) — Individual character scores

