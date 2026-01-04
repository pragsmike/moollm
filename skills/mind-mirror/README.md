# Mind Mirror

> *"Mirrors should reflect a little before throwing back images."*
> — Jean Cocteau (quoted in Mind Mirror)

---

## What Is Mind Mirror?

**Mind Mirror** is a personality modeling system based on Timothy Leary's 1985 software published by Electronic Arts. It transforms Leary's rigorous academic work (his 1950 PhD dissertation at UC Berkeley) into an interactive tool for self-discovery and character modeling.

In MOOLLM, Mind Mirror provides:
- **32 personality dimensions** across four "Thought Planes"
- **Dual vocabulary** (Plain Talk and Shrink-Rap)
- **0-7 rating scale** for each dimension
- **Character DNA** for NPCs and player avatars
- **Self-reflection exercises** for personal development

---

## The Academic Foundation

Before LSD, before Harvard, before counterculture, Timothy Leary was a legitimate psychologist. His 1950 PhD dissertation pioneered the **Interpersonal Circumplex** — a model that maps personality on a circle with two axes:

- **Vertical:** Dominance ↔ Submission
- **Horizontal:** Affiliation (Love) ↔ Hostility (Hate)

The *Annual Review of Psychology* called his 1957 book *The Interpersonal Diagnosis of Personality* "the most important book on psychotherapy of the year."

This wasn't mysticism — it was measurable, testable psychology.

---

## The Prison Escape: Theory Validated

On September 12, 1970, Leary provided the most dramatic validation of his own work.

Imprisoned with a 20-year sentence, he was administered psychological tests during intake — including his own **Leary Interpersonal Behavior Inventory**.

Knowing exactly what it measured, he answered strategically:
- Low dominance (won't challenge authority)
- High cooperation (will follow rules)
- Conventional interests (forestry, gardening)
- No leadership tendencies

**Result:** Assigned minimum security. Outdoor work detail.

Then he climbed a telephone wire over the prison fence.

> *"Understanding the test lets you pass the test. Consciousness of the game changes the game. The only prison is the one you cannot see."*

---

## Mind Mirror Software (1985)

Published by Electronic Arts when they still made "weird, beautiful things":

| | |
|---|---|
| **Design & Script** | Timothy Leary |
| **Programming** | Peter Van den Beemt, Bob Dietz |
| **Publisher** | Futique, Inc. / Electronic Arts |
| **Platforms** | Apple ][, Commodore 64, IBM PC |

### Leary's Introduction

> *"Hello, I'm Timothy Leary, welcome to Mind Mirror. For about two years I've been working on this software program. It allows you to digitalize your thoughts."*

> *"This is based upon my PhD thesis when I was a psychologist at the University of California in 1950. In those days I learned how to digitalize thoughts about yourself and how you'd like to be and your mother and your father."*

---

## The Four Thought Planes

Mind Mirror organizes personality into four circular maps, each with 8 dimensions arranged around a center.

### 1. BIO-ENERGY
*Life force, mood, vitality, temperament*

| Inner (Moderate) | Outer (Extreme) |
|------------------|-----------------|
| Energetic        | Wired           |
| Enthusiastic     | Vivacious       |
| Cheerful         | Silly           |
| Easy-Going       | Lazy            |
| Calm             | Lethargic       |
| Cautious         | Worried         |
| Serious          | Gloomy          |
| Restless         | Driven          |

### 2. EMOTIONAL INSIGHT
*Interpersonal style, approach to others*

| Inner (Moderate) | Outer (Extreme) |
|------------------|-----------------|
| Forceful         | Dominating      |
| Confident        | Charismatic     |
| Friendly         | Over-Friendly   |
| Docile           | Dependent       |
| Timid            | Submissive      |
| Touchy           | Resentful       |
| Irritable        | Angry           |
| Proud            | Arrogant        |

### 3. MENTAL ABILITIES
*Knowledge, creativity, imagination*

| Inner (Moderate) | Outer (Extreme) |
|------------------|-----------------|
| Well-Informed    | Know-It-All     |
| Innovative       | Visionary       |
| Creative         | Dreamy          |
| Impractical      | Unrealistic     |
| Uneducated       | Illiterate      |
| Sensible         | Imitative       |
| Conventional     | Unimaginative   |
| Practical        | Pedantic        |

### 4. SOCIAL INTERACTION
*Class, tolerance, sophistication*

| Inner (Moderate) | Outer (Extreme) |
|------------------|-----------------|
| Influential      | Snobbish        |
| Worldly          | Ultra-Sophisticated |
| Uninhibited      | Non-Conformist  |
| Uncultured       | Wild            |
| Lower-Class      | Unknown         |
| Unsophisticated  | Naive           |
| Moralistic       | Puritanical     |
| Respectable      | Upright         |

---

## The 16 Personality Scales

Mind Mirror features **dual vocabulary** — accessible Plain Talk and professional Shrink-Rap:

| Dimension | Plain Talk (+/-) | Shrink-Rap (+/-) |
|-----------|------------------|------------------|
| Energy | Peppy / Laid-Back | Hyper-Manic / Low-Energy |
| Intensity | Intense / Low-Key | Agitated / Tranquil |
| Mood | Happy / Sad | Euphoric / Melancholic |
| Commitment | Hesitant / Gung-Ho | Listless / Wholehearted |
| Assertiveness | Shy / Bossy | Passive / Dictatorial |
| Confidence | Cute / Cocky | Eager-to-Please / Haughty |
| Temperament | Sweet / Grumpy | Congenial / Hostile |
| Supportiveness | Encouraging / Whining | Nurturant / Complaining |
| Intelligence | Dumb / Knowledgeable | Ignorant / Intelligent |
| Organization | Organized / Flaky | Efficient / Disorganized |
| Creativity | Closed-Minded / Imaginative | Literal-Minded / Original |
| Adaptability | Ingenious / By-the-Book | Inventive / Narrow-Minded |
| Social Status | Social-Nobody / V.I.P. | Insignificant / Aristocratic |
| Conformity | Proper / Rowdy | Pillar-of-the-Community / Rebellious |
| Lifestyle | Straight-Arrow / Free-Living | Inhibited / Social-Maverick |
| Worldliness | Sophisticated / Square | Cosmopolitan / Small-Townish |

### Rating Scale

| Value | Meaning |
|-------|---------|
| 0 | Never |
| 2 | Rarely |
| 5 | Often |
| 7 | Always |

---

## Exercises from the Original Software

### Self Portrait
Compare your self with your ideal self.

> *"Every time you boot up MIND MIRROR you may want to update your rapidly changing self-image!"*

### Self-Range
Compare your best and worst selves.

Large gaps indicate volatility in that dimension.

### Role-Play Odyssey
Test empathy through 3,200 life simulation scenarios — from birth to transcendence.

---

## The Mirror Philosophy

Leary was clear about what Mind Mirror is NOT:

> *"Remember the title — it's a mirror. Now a best friend is your mirror because your mirror doesn't say 'well you bad boy get a haircut' or the mirror doesn't say 'hey turkey fix your tie' — you have to decide that."*

The mirror reflects. **You** decide what to do with the information.

---

## Using Mind Mirror in MOOLLM

### Character Profiles

Every character can have a Mind Mirror profile:

```yaml
# Abbreviated: just list notable traits
bartender:
  mind_mirror:
    bio_energy: [calm, serious]
    emotional: [confident, proud]
    mental: [well_informed, sensible]
    social: [worldly, uninhibited]
```

### Soul-Chat Influence

Mind Mirror dimensions affect how characters speak:

| Dimension | Voice Effect |
|-----------|--------------|
| calm | speaks slowly, pauses |
| confident | never apologizes unnecessarily |
| creative | uses unusual metaphors |
| uninhibited | occasionally vulgar |
| proud | never admits being wrong |

### Adventure NPCs

Mind Mirror profiles determine:
- How NPCs respond to player actions
- What advertisements they generate
- Decision-making in simulations

### Coatroom Modification

Costumes can modify Mind Mirror dimensions:

```yaml
# Wearing a cape
costume_effect:
  confident: +2
  influential: +1
  timid: -2
```

---

## The Ethics of Mind Mirror

See [ETHICS.md](./ETHICS.md) for a full discussion of:
- Using Leary's academic models respectfully
- The distinction between modeling and impersonation
- What Leary explicitly wanted (democratized self-discovery tools)
- How MOOLLM honors his legacy

**Short version:** We use his published academic framework and software design, not a simulation of him as a person.

---

## Bob Dietz on Leary's Vision

Bob Dietz, Leary's collaborator:

> *"His vision was way out there in the future... He always had these big vision things of wanting to do three-dimensionally and have the computer react to everything you said and with artificial intelligence."*

> *"He was all about self-empowerment, giving the users the keys to the kingdom."*

> *"I cannot begin to tell you how much Timothy Leary would have embraced and loved the notion of seeing Mind Mirror applied on the internet."*

---

## Protocol Symbols

| Symbol | Meaning |
|--------|---------|
| `MIND-MIRROR` | The personality modeling system |
| `THOUGHT-PLANE` | One of four circular dimensions |
| `SELF-PORTRAIT` | Compare self with ideal self |
| `SELF-RANGE` | Compare best and worst selves |
| `ROLE-PLAY-ODYSSEY` | Life simulation scenario |
| `PLAIN-TALK` | Accessible vocabulary mode |
| `SHRINK-RAP` | Professional vocabulary mode |

---

## Theme Song

From the original software:

> *"You can be anyone this time around*
> *You can be anything this time around*
> *It encourages me to change, to improve, to grow*
> *You can be anything this time around"*

This is the core message: **personality is not fixed**.

---

## Sources

| Source | Link |
|--------|------|
| Mind Mirror Text (Apple ][ extraction) | [donhopkins.com](https://donhopkins.com/home/mind-mirror.txt) |
| Mind Mirror Scales JSON | [donhopkins.com](https://donhopkins.com/home/mind-mirror.json) |
| USC Mind Mirror Archive | [scalar.usc.edu](https://scalar.usc.edu/works/timothy-leary-software/index) |
| Leary PhD Dissertation | [archive.org](https://archive.org/details/leary/leary.300dpi/mode/2up) |
| Interpersonal Circumplex | [Wikipedia](https://en.wikipedia.org/wiki/Interpersonal_circumplex) |
| Mind Mirror on Steam (2021) | [Steam](https://store.steampowered.com/app/1603300/Timothy_Learys_Mind_Mirror/) |

---

## Leary's Message

> *"I love my product. You know what my product is? The human mind and human hope and human enthusiasm."*

> *"You're the first generation in human history to know how to control your own nervous system, change your own reality. Tune in and take over! Blow your own mind, make up your own mind."*

---

## Dovetails With

- [representation-ethics/](../representation-ethics/) — Ethical personality modeling
- [hero-story/](../hero-story/) — Cards can include Mind Mirror profiles
- [card/](../card/) — Character cards embed Mind Mirror data
- [soul-chat/](../soul-chat/) — Mind Mirror influences character voice
- [adventure/](../adventure/) — NPCs have Mind Mirror profiles
- [coatroom/](../../examples/adventure-3/coatroom/) — Costumes modify dimensions

---

*"The ultimate intimacy is where you show them your personal database — you show your Mind Mirror."*
— Timothy Leary
