# Phase 2: Deliberation

**Topic:** How should we organize the source code to allow people to keep their worlds, adventures, etc. separate from the core skills and whatnot?
**Protocol:** Robert's Rules

## Opening Statements

### Maya 'Tilted Hat' Chen — Paranoid Realist (Devil's Advocate)

Who decides what counts as "core" and what counts as "user content"? And who benefits if someone's world accidentally depends on something we decide to change in the core later? I'm seeing a lot of assumptions here: that separation is always good, that "core" is stable, that people won't find ways to couple things anyway. What's the hidden cost of this separation? Are we creating a situation where core developers can break user content without knowing it? Or where users have to jump through hoops to do something simple? Who owns the boundary between "core" and "user"? That's where the power is. And why aren't we talking about migration paths? What happens to existing stuff when we redraw these lines?

### Frankie 'Kerouac' Rodriguez — Idealist (Opportunity Scout)

Strip away the jargon: what are we really trying to build here? This isn't about directory structure—it's about enabling people to create and share their worlds without being gatekept by the core system. What if we flip the question: instead of "how do we separate," what if we ask "how do we enable maximum creative autonomy while maintaining cohesion?" The structure should serve human flourishing: people should be able to experiment, fork, remix, and learn without breaking the core. What if this separation isn't a technical constraint but a creative opportunity? Can we design it so that the boundary itself becomes something people can play with? What does the structure look like if we optimize for curiosity and discovery, not just isolation?

### Joe 'Gusher' Castellano — Continuity Guardian (Historian)

We tried something like this in '09. Or rather, most codebases have tried some version of this. Plugin systems, module boundaries, namespace separation—these patterns exist for a reason, and they've failed for reasons too. The question isn't "should we separate," it's "how do we separate in a way that actually stays separated?" Here's what happened in the systems I've seen: someone starts with clean boundaries, then a deadline hits, someone takes a shortcut, and suddenly "user" code is calling "core" internals directly. The structure needs to make the right thing easy and the wrong thing hard. What worked before? Explicit contracts. Versioned interfaces. Clear ownership. What didn't work? Hoping developers would just "be good" about boundaries.

### Victor 'Vic Eyebrow' Okonkwo — Evidence Prosecutor (Evidence Checker)

Show me the data. What's the actual problem we're solving? How many worlds/adventures do we have now? How many contributors? What's the current coupling rate—how often does a core change break user content? I've read documentation on dependency management, plugin architectures, namespace isolation. The theory is clear, but show me evidence this specific structure works at this scale. What are the measurable criteria for success? Reduced breakage rate? Faster iteration? Lower onboarding friction? Don't tell me "separation is good"—show me the numbers that prove this particular separation is better than alternatives. And what's the proof that the structure itself won't become a maintenance burden? Every abstraction has a cost.

### Tammy 'Silent' Park — Systems Thinker (Systems Analyst)

[Long silence]

Have we considered that changing the structure changes the incentive structure for everyone adjacent to the problem? If we make "user content" too separate, do we reduce the chances that users contribute back improvements to core? If we make it too easy to fork, do we fragment the community? What happens three moves downstream: someone builds a world that depends on a specific core behavior, then core changes, then that world breaks, then the user fixes it by copying core code into their world, then we have duplication and drift. The separation isn't just technical—it's social. It determines who can modify what, who feels ownership, who gets blamed when things break. What feedback loops does this create? How does it affect the learning curve for new contributors? The structure should encourage the behaviors we want, not just organize files.

### Samir 'Sam' Patel — Operational Realist (Operational Reality Check)

Okay, but what happens at 2 a.m. when someone's world breaks in production and we need to debug it? If the separation is too strict, can we even see into their code? If it's too loose, do we get paged for bugs that aren't ours? The structure needs to answer: what's the rollback plan if a world update goes bad? How do we test that core changes don't break user content? How do we onboard someone new who needs to touch both sides? I've shipped enough systems to know the hard part isn't the architecture—it's keeping it alive in messy reality. What's the failure mode if someone needs to do something that doesn't fit the separation? Do they work around it cleanly or do they create technical debt? The structure should make the operational realities explicit: deployment, testing, debugging, monitoring. If we can't test it, observe it, or roll it back, it's not real separation.

---

## Initial Positions Summary

| Member | Stance | Confidence | Key Concern |
|--------|--------|------------|-------------|
| **Maya** | Suspicious | High | Power dynamics and hidden costs of separation |
| **Frankie** | Optimistic | Medium | Creative autonomy and opportunity, not just isolation |
| **Joe** | Cautious | High | Precedent shows boundaries erode without enforcement |
| **Vic** | Skeptical | Medium | Need evidence and measurable success criteria |
| **Tammy** | Observant | Medium | Systems effects on community and feedback loops |
| **Samir** | Pragmatic | High | Operational reality: debugging, testing, rollbacks |

---

## Key Tensions Identified

1. **Separation vs. Integration:** Maya and Samir worry separation creates operational blind spots; Frankie sees it as enabling creativity
2. **Enforcement vs. Flexibility:** Joe wants strong boundaries; Frankie wants permeable, explorable boundaries
3. **Evidence vs. Vision:** Vic demands data; Frankie wants to optimize for human flourishing
4. **Technical vs. Social:** Samir focuses on operational mechanics; Tammy maps community dynamics

---

**Status:** DELIBERATING
**Next:** Structured debate on Tensions 1 & 2.
