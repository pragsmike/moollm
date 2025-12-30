# MOOLLM Kernel
## Low-Level Operating System Protocols

*"The orchestrator is the operating system. The LLM is the CPU."*

---

## What is the Kernel?

The MOOLLM kernel is the **minimal, stable core** that all higher-level
protocols and skills depend on. It provides:

1. **Tool Execution** — File ops, search, sandboxed execution
2. **Context Assembly** — Building prompts from working sets
3. **Event Logging** — Append-only audit trails
4. **Memory Management** — Hot/cold hints, summarization
5. **Self-Healing** — Robust-first repair and bootstrap

The kernel does NOT encode semantics about:
- What "memory palaces" are
- What "adventure rooms" mean
- How "trading cards" work
- Character personalities

Those are **skills** (userland protocols).

---

## Modular Architecture

The kernel is designed to run on **multiple orchestrators**:

```
┌─────────────────────────────────────────┐
│         constitution-core.md            │
│         (Universal Principles)          │
├─────────────────────────────────────────┤
│   drivers/cursor.yml  │  drivers/...    │
│   (Orchestrator-Specific Adaptations)   │
├─────────────────────────────────────────┤
│   Cursor  │  Claude Code  │  Custom     │
│   (Orchestrator Runtime)                │
└─────────────────────────────────────────┘
```

### Constitution Layers

| Layer | File | Purpose |
|-------|------|---------|
| Core | `constitution-core.md` | Universal principles |
| Full | `constitution-template.md` | Complete template (custom) |
| Driver | `drivers/*.yml` | Orchestrator adaptations |

### Available Drivers

| Driver | Tier | Key Differences |
|--------|------|-----------------|
| `cursor.yml` | 4 | No `why` param, convention-based append |
| `claude-code.yml` | 5 | MCP support, can add custom tools |
| `custom.yml` | 6 | Full control, all features enforced |
| `generic.yml` | 1 | Minimal assumptions, maximum compat |

---

## Kernel Files

| File | Purpose |
|------|---------|
| `constitution-core.md` | Universal principles (orchestrator-independent) |
| `constitution-template.md` | Full template for custom orchestrators |
| `tool-calling-protocol.md` | How tools are defined and called |
| `context-assembly-protocol.md` | How prompts are built from files |
| `memory-management-protocol.md` | Hot/cold, summaries, GC |
| `self-healing-protocol.md` | MFM-inspired repair |
| `event-logging-protocol.md` | Append-only audit |
| `drivers/` | Orchestrator-specific configurations |

---

## Capability Tiers

Different orchestrators provide different capabilities:

| Tier | Capabilities | Examples |
|------|-------------|----------|
| 0 | Text only | Basic chat |
| 1 | File read | Most UIs |
| 2 | File read/write | IDEs |
| 3 | + Search | Cursor, Claude Code |
| 4 | + Execution | Cursor, Claude Code |
| 5 | + Custom tools (MCP) | Claude Code |
| 6 | + Full kernel control | Custom only |

### Feature Availability by Tier

| Feature | Tier 1-2 | Tier 3-4 | Tier 5 | Tier 6 |
|---------|----------|----------|--------|--------|
| `why` parameter | ❌ Convention | ❌ Convention | ⚠️ Via MCP | ✅ Enforced |
| Append-only | ❌ Convention | ❌ Convention | ⚠️ Via MCP | ✅ Enforced |
| Event logging | ❌ Manual | ⚠️ Markdown | ⚠️ Via MCP | ✅ JSONL |
| Working set | ❌ Manual | ⚠️ Reference | ⚠️ Reference | ✅ Integrated |
| Hot/cold hints | ❌ Manual | ⚠️ Reference | ⚠️ Reference | ✅ Automated |

**Key:** ✅ = Enforced, ⚠️ = Supported, ❌ = Convention only

---

## The Kernel Contract

```yaml
kernel_guarantees:
  - Tool calls execute or fail cleanly
  - Context fits in token budget
  - Events are never lost
  - State can always be recovered
  - Missing files trigger repair, not crash

kernel_does_not_guarantee:
  - Meaningful output (that's the LLM's job)
  - Correct planning (that's emergent)
  - User satisfaction (that's the skill's job)
```

---

## Integration with MOOLLM Protocols

The kernel sits beneath all MOOLLM protocols:

```
┌─────────────────────────────────────────┐
│     MOOLLM Protocols (P-0.x, P-1.x)     │
│     Trading Cards, Rooms, Characters    │
├─────────────────────────────────────────┤
│     Skills / Userland Protocols         │
│     Memory Palaces, Adventures, etc.    │
├─────────────────────────────────────────┤
│     KERNEL                              │
│     Tools, Context, Memory, Repair      │
├─────────────────────────────────────────┤
│     LLM (stateless token predictor)     │
└─────────────────────────────────────────┘
```

---

## Design Philosophy

Inspired by:
- **Dave Ackley's Robust-First Computing** — Survivability over correctness
- **Movable Feast Machine** — Local repair, homeostatic goals
- **SELF Language** — Prototypes and delegation
- **Unix Philosophy** — Simple tools, composition

> *"Make the kernel boring so the protocols can be exciting."*

---

**See also:**
- `../MOOLLM-PROTOCOLS.md` — Protocol compendium
- `../MOOLLM-MANIFESTO.md` — Philosophy
- `../skills/` — Userland protocols
- `../schemas/` — Data formats
