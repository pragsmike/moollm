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

## Round 1: Separation vs. Integration

**Chair:** "The floor is open. Let's address the first tension identified: Separation versus Integration. Frankie, you argued for maximum autonomy. Maya and Samir, you flagged the hidden costs of that separation. Maya, would you like to open this round?"

### Maya 'Tilted Hat' Chen — Paranoid Realist

"Frankie, I love the poetry, truly. 'Sonic landscapes' sound great. But when you say 'maximum creative autonomy,' I hear 'no accountability.' If we let users fork everything because we want them to 'flourish,' who pays the bill when they fork a security vulnerability? Who fixes their 'art' when the core API changes and their world goes dark? Autonomy without maintenance isn't freedom; it's just abandonment. You're selling them a dream house but not telling them they have to fix the plumbing themselves."

### Frankie 'Kerouac' Rodriguez — Idealist

"That's exactly it, Maya! You see 'abandonment,' I see 'ownership.' If they fix the plumbing, they *learn* plumbing. We're not building a hotel where guests are helpless; we're building a workshop. If we lock down the core so tight that they can't break anything, we also ensure they can't make anything truly new. Sure, if they fork it, they own the risk. But make that explicit! Don't treat them like children because you're afraid of a lawsuit. Give them the keys, tell them 'this car has no brakes if you cut this wire,' and let them drive."

### Samir 'Sam' Patel — Operational Realist

"Okay, let's look at the blast radius of 'letting them drive.' Frankie, if they fork a core skill—say, the `memory` module—because they want to add a 'dream logic' feature... and then we patch a critical bug in `memory`... they don't get the patch. Six months later, their world is running a vulnerable, buggy version of `memory`. They file a bug report saying 'MOOLLM is broken.' Now *my* team is debugging a six-month-old fork they didn't even know existed. That's not just their problem; that's an operational nightmare for us. 'Ownership' sounds nice until the on-call pager goes off."

### Tammy 'Silent' Park — Systems Thinker

[Silence]

"This isn't binary. You're talking about 'Fork' vs. 'Lock.' There's a middle state: 'Extend.' What if the structure encourages *extensions* over *modifications*? If the directory layout makes it easier to write a plugin than to copy-paste the core, people will write plugins. We're designing the path of least resistance. Currently, dragging a file is easier than learning an API. If we want them to integrate safely, we have to make the 'safe' way the 'lazy' way."

### Victor 'Vic Eyebrow' Okonkwo — Evidence Prosecutor

"Show me an example of that working, Tammy. I've seen a dozen 'plugin architectures' that just became 'undocumented dependency hell.' Do we have data on user behavior in the current system? How many people are actually modifying core skills right now? If it's zero, we're arguing about ghosts. If it's fifty percent, we have a crisis. Before we redesign the whole architecture to solve a theoretical 'forking' problem, show me the diffs. Are users actually breaking things, or are we just afraid they might?"

### Joe 'Gusher' Castellano — Continuity Guardian

"Vic's right about the ghosts. But I'll tell you what happened in '09 with the old legacy bot. We let people script their own rooms. Within a month, half the scripts depended on a bug in the entrance code. When we fixed the bug, every room locked shut. Users didn't 'learn plumbing,' Frankie. They quit. We lost thirty percent of the userbase in a week. That's the history. Separation needs to be backward-compatible, or it's a suicide pact."

---

## Round 1 Analysis

**Emerging Consensus:**
*   **Tammy & Joe:** Uncontrolled "forking" leads to unmaintainable debt (Joseph's '09 example supports this).
*   **Samir:** Ops cost of forks is externalized to the core team.
*   **Frankie:** Still fighting for the *possibility* of deep modification, even if risky.

**New Tension:**
*   **"Lazy" Design (Tammy):** Can we structure directories so the *easiest* action is the *safest* one?
*   **Evidence Gap (Vic):** Do we actually know what users are doing right now?

**Status:** DELIBERATING
**Next:** Round 3: Closing Statements & Consensus

---

## Round 2: The Lazy Path

**Chair:** "Tammy, you proposed a 'Lazy Path' where doing the right thing (extension) is easier than the wrong thing (forking/breaking core). Can you make that concrete? What does the directory structure actually look like on disk?"

### Tammy 'Silent' Park — Systems Thinker

"It looks like 'Scope Precedence.' We stop thinking of 'Core' vs 'User' as a binary and start thinking of them as layers. The 'Laziest' thing a user can do is create a new directory.

"Propsoed Structure:
```
moollm/
  k-lines/          # (Formerly 'skills' or 'core') - READ ONLY reference
    standard/
      memory.yml
      bootstrap.yml
  
  worlds/           # User space - READ/WRITE
    my-adventure/
      ROOM.yml
      
      # The Lazy Extension Pattern:
      # If I want to change how memory works, I don't edit core. 
      # I just drop a file here.
      k-lines/      
        memory.yml  # <--- Shadows core/memory.yml for THIS world only
```

"Why is this lazy? Because `cp` is easier than `git fork`. If they want to change behavior, they just copy the skill to their folder and edit it. The system automatically prioritizes the local version. They don't break the global system, only their own room."

### Samir 'Sam' Patel — Operational Realist

"I see the appeal, but you've just moved the 'hidden dependency' problem. Now, when I'm debugging `my-adventure`, I have to check: is the bug in `core/memory` or `local/memory`? If they shadow `core/memory`, they miss security updates to the real memory skill. It's the same outdated-fork problem, just localized.

"However... it *does* solve the 'blast radius' problem. If their local memory skill is broken, it only crashes their world, not the whole server. I can live with that *if* the system logs clearly: `WARNING: 'my-adventure' is running a shadowed version of 'memory'`."

### Maya 'Tilted Hat' Chen — Paranoid Realist

"Wait. If local shadows global... what stops a malicious world from shadowing the `login` or `auth` protocol? A user enters 'The Nice Park,' thinks they're using the standard secure login, but actually they're talking to `worlds/nice-park/k-lines/login.yml` which steals their credentials. The 'Lazy Path' sounds like a 'Lazy Hack' for attackers. Who controls the precedence list?"

### Frankie 'Kerouac' Rodriguez — Idealist

"Maya, you're ruining the jam session! But... okay, valid point. But look at the flip side: this structure means I can build a world where the laws of physics (the protocols) are effectively different, without asking permission. I can make a 'No-Memory World' just by creating an empty `memory.yml`. That's powerful. 

"Maybe the fix for Maya's fear is visual? If I'm in a room with shadowed protocols, the UI should look different. 'You are entering a Non-Standard Reality.' Like a HTTPS warning, but cooler."

### Joe 'Gusher' Castellano — Continuity Guardian

"Standard library code (Core) must be distinct from User code. That's good. But I'm worried about the name `k-lines`. We call them `skills` now. Changing the name to `k-lines` in the directory structure confuses old contributors. Let's stick to `skills/` for the concept, but maybe `core/skills` vs `local/skills`?

"Also, we need a way to 'eject.' If my local skill becomes really good, how do I promote it to core? The structure should show the path: `local/` -> `staging/` -> `core/`."

---

## Round 2 Analysis

**Emerging Consensus:**
*   **Shadowing Pattern:** Everyone seems to accept the "local shadows global" pattern *if* it is scoped strict to the world (solving Samir's blast radius concern).
*   **Security Risk:** Maya is right; shadowing critical auth/system protocols is dangerous. We need a "Protected Mode" or "Final" keyword for some core skills.
*   **Terminology:** Joe prefers sticking to recognized names (`skills` over `k-lines`) for continuity.

**Draft Proposal for Resolution:**
1.  **Root Split:** `moollm/core` (System) vs `moollm/worlds` (User).
2.  **Precedence:** `worlds/.../skills` overrides `core/skills`.
3.  **Safety:** A whitelist of "locked" protocols (like `security`, `payments`) that cannot be shadowed.

**Status:** VOTING
**Next:** Phase 3: Resolution Artifact Generation

---

## Round 3: Closing Statements & Consensus

**Chair:** "We have a draft proposal: Segregate `core` and `worlds`. Allow `worlds` to shadow skills for 'Lazy Extension.' Enforce a 'Locked List' for safety. Let's do a final whip-around to refine the naming and confirm consensus."

### Frankie 'Kerouac' Rodriguez — Idealist

"I'm on board. This structure feels like a city. We have the public infrastructure (Core) that works for everyone, but inside my house (World), I can paint the walls whatever color I want. If I want to replace gravity with neon lights in my living room, I can. That's the creative autonomy I wanted. I accept the 'Locked List' as building codes—you can't remove the fire exits."

### Maya 'Tilted Hat' Chen — Paranoid Realist

"I'm cautiously optimistic. Calling it 'Shadowing' makes the risk explicit. As long as the `security`, `auth`, and `billing` protocols are on that Locked List—and the `bootstrap` probe verifies they haven't been touched—I can sign off. But I want the directory names to be honest. Don't call it `core` if it's actually a `kernel` that controls everything."

### Joe 'Gusher' Castellano — Continuity Guardian

"I agree with Maya on the naming. `Core` implies a center, but `Kernel` implies the operating system—the part you don't touch unless you're a driver. Let's use `kernel/` for the immutable stuff and `worlds/` for the user stuff. And let's keep `skills/` as the standard folder name. 

"So:
- `kernel/skills/` (Global)
- `worlds/my-world/skills/` (Local Shadow)
"

### Samir 'Sam' Patel — Operational Realist

"From an Ops perspective, this is a win. I can put `kernel/` on a read-only mount for production containers, and mount `worlds/` as a separate volume. If a world gets corrupted, I wipe the volume, the kernel stays safe. The separation of concerns is clean. I'm a 'Yes'."

### Tammy 'Silent' Park — Systems Thinker

"The metaphor holds. 'Kernel is the Constitution; Worlds are the States.' States have local laws (local skills) but cannot override the Constitution (Locked Protocols). This structure balances the feedback loops: users can experiment locally, and if a local skill proves stable and useful, we have a clear path to 'federalize' it into the Kernel. It encourages evolution."

### Victor 'Vic Eyebrow' Okonkwo — Evidence Prosecutor

"I'll suspend my disbelief until I see the implementation plan in the Resolution. But logically, this structure addresses the failure modes we identified. It provides the isolation I asked for. I consent to move to voting."

---

## Final Consensus

The committee has reached alignment on the **"Federalist Directory Model"**:

1.  **Directory Split:**
    *   `kernel/` (System): Contains standard library, drivers, and immutable protocols.
    *   `worlds/` (User): Contains independent adventures, rooms, and narratives.

2.  **Extension Mechanism (Shadowing):**
    *   Worlds can define a local `skills/` directory.
    *   Local skills *override* Kernel skills of the same name within that world scope.

3.  **Safety Protocol (The Locked List):**
    *   Critical protocols (Auth, Billing, Kernel Integrity) are marked `final`.
    *   The System prohibits shadowing these protocols; attempts to do so raise a boot error.

**Status:** DELIBERATION COMPLETE
**Next:** Moving to **Phase 3: Resolution**. The Chair will now draft `03-resolution.yml` for ratification.