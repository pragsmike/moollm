# PR: Explicit Impersonation & Drag Tribute Ethics

**Date:** 2026-01-09  
**Branch:** don-adventure-4-run-1  
**Author:** Claude (with Don Hopkins)

---

## Summary

Extended the representation-ethics framework to include explicit impersonation patterns where the **naming convention itself provides the ethical framing**.

---

## The Core Insight

> **The label IS the disclaimer.**

When a character is named "Elvis Impersonator" or "Cher-ity Case", no additional ethical framing is needed — the name itself declares "this is not the real person."

---

## New Abstraction Levels

Added to the representation ethics spectrum:

| Level | Example | Safety | Why |
|-------|---------|--------|-----|
| **explicit-impersonator** | "Elvis Impersonator performs tonight" | HIGH | The word "impersonator" IS the disclosure |
| **drag-celebrity-tribute** | "Cher-ity Case takes the stage" | HIGH | Pun name + drag context = unmistakable tribute |

---

## Types of Explicit Impersonation

### 1. Labeled Impersonator
```yaml
examples:
  - "Elvis Impersonator"
  - "Celebrity Impersonator Night"  
  - "The Australian Pink Floyd Show (tribute band)"
  - "Weird Al Yankovic (parody artist)"
```
The word "impersonator/tribute/parody" **is** the ethical protection.

### 2. Drag Celebrity Tribute
```yaml
examples:
  - "Cher-ity Case"
  - "Sharon Needles"
  - "Chad Michaels as Cher"
  - "Snatch Game contestants"
```
The **pun name** + **theatrical drag context** = clear performance framing.

### 3. Satirical Character
```yaml
examples:
  - "Tina Fey as Sarah Palin"
  - "Alec Baldwin as Trump"
  - "Any SNL political cold open"
```
Sketch comedy context + known actors = obvious performance.

---

## Precedents

| Tradition | Why It's Ethical |
|-----------|------------------|
| **Elvis Impersonators** | Beloved industry, everyone knows it's tribute |
| **Tribute Bands** | The word "tribute" frames everything |
| **Snatch Game** | Drag queens explicitly "playing" celebrities |
| **SNL Impressions** | Sketch comedy context, known actors |
| **Historical Re-enactors** | Educational performance, clearly labeled |
| **Weird Al** | Parody is its own ethical category |

---

## Files Changed

### Modified
- `skills/representation-ethics/CARD.yml`
  - Added `explicit-impersonator` and `drag-celebrity-tribute` to abstraction-levels
  - Expanded the spectrum diagram
  - New `explicit-impersonation` section with types and precedents

- `skills/representation-ethics/SKILL.md`
  - Added **Frame 6: The Drag Celebrity Tribute**
  - Snatch Game precedent documented
  - Naming conventions table

- `examples/adventure-4/characters/real-people/ROOM.yml`
  - Added same abstraction levels to the local ethical guidance

---

## MOOLLM Application

In MOOLLM adventures, characters can be framed as:

```yaml
# These are all ethically safe:

- name: "The Elvis Impersonator"
  type: tribute_performer
  # The word "impersonator" = automatic framing

- name: "Cher-ity Case"  
  type: drag_tribute
  evokes: "Cher"
  # The pun name = automatic framing

- name: "Tonight's Bowie Tribute Act"
  type: tribute_band
  # The word "tribute" = automatic framing
```

---

## The Spectrum (Updated)

```
MOST ABSTRACT ←─────────────────────────────────────────────→ MOST DIRECT

Tradition  Inspired  Homage   Impersonator  Drag-Tribute  Performance  Bio    Quote
activation character (renamed) (labeled)    (pun-name)    embodiment  portrayal (cited)
```

All levels can be ethical with appropriate framing — and for labeled impersonators and pun-name tributes, **the name itself IS the framing**.

---

## Related

- `skills/representation-ethics/` — Full ethical framework
- `skills/incarnation/` — Character autonomy principles  
- `examples/adventure-4/characters/real-people/` — Where tributes to real people live

---

## Quotes

> "The word 'impersonator' carries the disclaimer within itself."

> "Cher-ity Case ≠ Cher. The pun declares the fiction."

> "The Snatch Game precedent: everyone knows it's drag queens playing celebrities."
