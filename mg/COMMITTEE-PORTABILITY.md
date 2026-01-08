# Running MOOLLM Committee Sessions in Other Chat UIs

MOOLLM is designed to be **portable** — it's "protocols the model follows," not code. You can run committee sessions (or any MOOLLM session) in **any chatbot UI** that can read files, including:

- **Claude (Anthropic Chat/Web)**
- **ChatGPT (Web Interface)**
- **Google AI Studio (Gemini)**
- **Perplexity**
- **Any LLM with file reading capability**

---

## How MOOLLM Portability Works

MOOLLM is **orchestrator-agnostic**:

1. **Character files are YAML** — readable by any LLM
2. **Protocols are instructions** — not code dependencies
3. **SPEED-OF-LIGHT simulation** — all characters debate in **one LLM call** (no file I/O between turns)
4. **Graceful degradation** — works at any capability tier (see below)

The key insight: **The LLM IS the coherence engine.** It simulates multiple agents simultaneously by reading their character files and following the protocol.

---

## Quick Start: Running Your Committee Session Elsewhere

### Step 1: Prepare the Character Files

You need to provide the character files to the other LLM. Options:

**Option A: Copy Character Files**
Copy the character YAML files from `mg/characters/` and paste them into your chat, or attach them as files if the UI supports file uploads.

**Option B: Point to Repository**
If the other LLM can access GitHub or your repository, point it to:
- `mg/characters/maya-tilted-hat.yml`
- `mg/characters/frankie-kerouac.yml`
- `mg/characters/joe-gusher.yml`
- `mg/characters/vic-eyebrow.yml`
- `mg/characters/tammy-silent.yml`
- `mg/characters/samir-patel.yml`

**Option C: Create a Single Context File**
Create a `COMMITTEE-CONTEXT.md` file with all character files embedded:

```markdown
# Committee Session Context

## Characters

### Maya 'Tilted Hat' Chen
```yaml
[Paste full character YAML here]
```

### Frankie 'Kerouac' Rodriguez
```yaml
[Paste full character YAML here]
```

[... and so on for all 6 members]
```

### Step 2: Provide the Protocol Instructions

Copy this prompt template and adapt it for your topic:

---

## Prompt Template for Other UIs

```
I'm running a MOOLLM adversarial committee session. Here's the protocol:

**PROTOCOL: ADVERSARIAL-COMMITTEE**

You will simulate a committee of 6 characters with opposing propensities who debate a topic using Robert's Rules of Order. All characters speak in ONE LLM call (SPEED-OF-LIGHT simulation).

**Committee Members:**
[Attach or paste character files here, or reference file paths]

**Current Topic:**
[Your topic here]

**Current Phase:** Opening Statements (CONVENE phase)

**Protocol Rules:**
1. Each character has a unique propensity type, risk tolerance, epistemology, and debate role
2. Characters speak authentically based on their propensities
3. All opening statements happen in this single response
4. Characters challenge assumptions, surface blind spots, and explore the topic from different angles
5. Use Robert's Rules when needed (one speaker at a time, motions, seconds, etc.)

**Format:**
Present each character's opening statement in sequence, clearly labeled:
- Maya 'Tilted Hat' Chen (Paranoid Realist / Devil's Advocate): ...
- Frankie 'Kerouac' Rodriguez (Idealist / Opportunity Scout): ...
- Joe 'Gusher' Castellano (Continuity Guardian / Historian): ...
- Victor 'Vic Eyebrow' Okonkwo (Evidence Prosecutor / Evidence Checker): ...
- Tammy 'Silent' Park (Systems Thinker / Systems Analyst): ...
- Samir 'Sam' Patel (Operational Realist / Operational Reality Check): ...

After opening statements, provide a summary of:
- Key tensions identified
- Initial positions and confidence levels
- Evidence gaps that need to be addressed

Now run the CONVENE phase for the topic: [YOUR TOPIC HERE]
```

---

## Adapting for Specific UIs

### Claude (Anthropic Chat/Web)

**Advantages:**
- Excellent at following complex instructions
- Good at maintaining character voices
- Can handle long context with multiple files

**Setup:**
1. Create a new chat
2. Upload or paste all 6 character files
3. Paste the protocol prompt above
4. Ask Claude to run the session

**Example:**
```
I've attached 6 character YAML files. Please read them and run a CONVENE phase where each character gives an opening statement on this topic: "How should we organize source code to separate user worlds/adventures from core skills?"

Follow the ADVERSARIAL-COMMITTEE protocol: all characters speak in this single response, each maintaining their unique voice based on their propensity type.
```

### ChatGPT (Web Interface)

**Advantages:**
- Supports file attachments
- Can handle multi-character simulation
- Good context retention

**Setup:**
1. Start a new conversation
2. Attach character files (if supported) or paste them
3. Use the prompt template above

**Limitation:** ChatGPT may need reminders to maintain character voices throughout longer sessions.

### Google AI Studio (Gemini)

**Advantages:**
- Strong multi-agent simulation
- Good at following structured protocols

**Setup:**
1. Open AI Studio
2. Create a new prompt
3. Paste character files + protocol instructions
4. Run the simulation

### Perplexity

**Advantages:**
- Can pull from web sources
- Good at evidence-based reasoning

**Note:** Perplexity is optimized for research, not character simulation. You may need to be more explicit about roleplay vs. factual responses.

---

## Running DELIBERATE Phase

After opening statements, continue with debate rounds:

```
Now run DELIBERATE phase — Round 1:
- Each character responds to at least one other character's opening statement
- Maintain authentic voices based on propensities
- Surface specific tensions and evidence gaps
- Follow Robert's Rules (wait for recognition, make motions, etc.)
- All debate happens in this single response
```

---

## Key Principles for Portability

### 1. SPEED-OF-LIGHT Simulation
- **All characters speak in ONE LLM call**
- No file I/O between turns
- The LLM simulates the entire committee simultaneously

### 2. Character Authenticity
- Characters speak based on their **propensity type**, **risk tolerance**, **epistemology**, and **debate role**
- Each character has a **signature voice** and **surfaces specific concerns**

### 3. Productive Tension
- Characters have **opposing propensities** (paranoid vs. idealist, evidence vs. systems thinking)
- This creates **genuine debate** that surfaces blind spots
- The goal is **exploration**, not immediate consensus

### 4. Graceful Degradation
MOOLLM works at different capability tiers:

| Tier | Capabilities | Works In |
|------|-------------|----------|
| 0 | Text only (LLM simulates based on instructions) | **Any LLM** |
| 1 | File read (can read character files) | Most UIs |
| 2 | File read/write (can save session transcripts) | IDEs, some UIs |
| 3 | + Search (can find characters dynamically) | Cursor, Claude Code |
| 4 | + Execution (can run scripts) | Cursor, Claude Code |
| 5 | + Custom tools (MCP) | Claude Code |

**At Tier 0:** Just paste the character files and protocol instructions — the LLM can still simulate the committee!

---

## Example: Full Session in Claude Chat

```
I want to run a MOOLLM adversarial committee session. Here are the 6 committee members:

[Paste all 6 character YAML files]

Topic: "How should we organize source code to separate user worlds/adventures from core skills?"

Protocol: ADVERSARIAL-COMMITTEE
- Simulate all 6 characters debating in ONE response
- Each character speaks authentically based on their propensity
- Use Robert's Rules for structure
- Surface tensions, evidence gaps, and blind spots

Phase 1: CONVENE — Each character gives an opening statement (2-3 sentences)
Phase 2: DELIBERATE — Round 1 of debate (each responds to at least one other)

Start with Phase 1.
```

---

## What Gets Lost in Different UIs?

**What works everywhere:**
- Character simulation (YAML files are just data)
- Multi-agent debate (LLM can simulate multiple voices)
- Protocol instructions (just text)

**What's easier in Cursor/Claude Code:**
- Automatic file reading (characters auto-loaded)
- Session persistence (COMMITTEE.yml, COMMITTEE-SESSION.md auto-updated)
- Structured workflows (FORM-SMART, CONVENE, DELIBERATE as commands)

**Workaround:** In other UIs, you manually provide context each time, but the **core simulation works the same way**.

---

## Reference: Core MOOLLM Files for Committee Sessions

| File | Purpose | Needed? |
|------|---------|---------|
| `mg/COMMITTEE.yml` | Committee structure and members | Optional (just for tracking) |
| `mg/COMMITTEE-SESSION.md` | Session transcript | Optional (you can create your own) |
| `mg/characters/*.yml` | Character definitions | **Required** |
| `skills/adversarial-committee/SKILL.md` | Full protocol specification | Optional (helpful for advanced use) |
| `skills/adversarial-committee/CARD.yml` | Machine-readable interface | Optional (only needed by orchestrators) |

**Minimum viable:** Just the character YAML files + protocol instructions in plain text.

---

## Tips for Best Results

1. **Be explicit about format:** Tell the LLM exactly how to present responses (labeled sections, clear speaker identification)

2. **Reference character traits:** Remind the LLM to use each character's "propensity", "debate_role", and "voice" fields

3. **One call per phase:** Keep opening statements, each debate round, voting, etc. as separate requests (or one big request if the UI supports it)

4. **Save transcripts:** Copy the LLM's responses into a markdown file if the UI doesn't auto-save

5. **Iterate:** If characters don't sound authentic, provide more context from their YAML files (beliefs, speaking_style, relationships)

---

## Next Steps

After running a session in another UI, you can:

- Copy the transcript back to `mg/COMMITTEE-SESSION.md`
- Update `mg/COMMITTEE.yml` with status
- Continue the session in Cursor for file management
- Use the session outputs to inform decisions

**MOOLLM is portable by design.** The filesystem-based state (COMMITTEE.yml, character files) can be read anywhere, and the protocols can be followed by any LLM that can read instructions.

