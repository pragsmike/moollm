# Event Logging Protocol
## Append-Only Audit Trail

---

## 1. Overview

Every action in MOOLLM is logged to an append-only event stream.
This provides:
- Perfect audit trail
- Replay capability  
- Debugging support
- Analytics foundation

**Invariant:** `events.jsonl` is APPEND-ONLY. Never modify, never delete.

---

## 2. Event Schema

```yaml
event:
  type: string          # Event category
  timestamp: string     # ISO 8601
  session_id: string?   # Session context
  
  # Type-specific fields...
  
  metadata:
    protocol: string    # Protocol version
    sequence: int?      # Event sequence number
```

---

## 3. Event Types

### Session Events

```jsonl
{"type":"session_start","timestamp":"2025-12-30T12:00:00Z","session_id":"sess-001","protocol":"EVENT-LOG/0.1"}
{"type":"session_end","timestamp":"2025-12-30T14:30:00Z","session_id":"sess-001","reason":"user_exit","stats":{"turns":45,"tools":123}}
```

### Tool Events

```jsonl
{"type":"tool_call","timestamp":"...","tool":"fs.read","args":{"path":"x.md","why":"Check content"},"call_id":"call-001"}
{"type":"tool_result","timestamp":"...","tool":"fs.read","call_id":"call-001","success":true,"result":{"lines":50},"duration_ms":12}
{"type":"tool_error","timestamp":"...","tool":"fs.read","call_id":"call-001","error":{"code":"NOT_FOUND","message":"File not found"}}
```

### Model Events

```jsonl
{"type":"model_input","timestamp":"...","tokens":2500,"files_in_context":["a.md","b.md"]}
{"type":"model_output","timestamp":"...","tokens":500,"tool_calls":1,"text_length":1200}
{"type":"model_turn","timestamp":"...","turn":15,"input_tokens":2500,"output_tokens":500}
```

### Memory Events

```jsonl
{"type":"context_assembly","timestamp":"...","budget":28000,"used":23456,"included":["a.md"],"excluded":["b.md"]}
{"type":"working_set_update","timestamp":"...","action":"add","path":"new.md","priority":0.7}
{"type":"cache_advice","timestamp":"...","hot_added":["a.md"],"cold_added":["b.md"]}
{"type":"gc_run","timestamp":"...","trigger":"budget","freed_tokens":5000,"files_affected":3}
{"type":"summary_created","timestamp":"...","source":["a.md","b.md"],"target":"summaries/ab.md"}
```

### Repair Events

```jsonl
{"type":"repair","timestamp":"...","demon":"checklist_repairer","action":"created","path":"hot.yml"}
{"type":"repair","timestamp":"...","demon":"membrane_keeper","action":"moved","from":"stray.md","to":".agent/stray/stray.md"}
{"type":"bootstrap","timestamp":"...","files_created":["output.md","events.jsonl","working_set.yml"]}
```

### User Events

```jsonl
{"type":"user_message","timestamp":"...","length":150,"attachments":["file.png"]}
{"type":"user_approval","timestamp":"...","action":"tool_call","tool":"terminal.run","approved":true}
{"type":"user_edit","timestamp":"...","file":"output.md","change":"added paragraph"}
```

### Error Events

```jsonl
{"type":"error","timestamp":"...","code":"BUDGET_EXCEEDED","message":"Context too large","recovery":"truncated"}
{"type":"warning","timestamp":"...","code":"MISSING_SIDECAR","message":"File lacks .meta.yml","path":"orphan.md"}
```

---

## 4. Event File Format

### Location
```
.agent/sessions/<session_id>/events.jsonl
```

### Format
- JSON Lines (one JSON object per line)
- UTF-8 encoded
- Newline-delimited
- No trailing comma

### Example
```jsonl
{"type":"session_start","timestamp":"2025-12-30T12:00:00Z","session_id":"sess-001"}
{"type":"tool_call","timestamp":"2025-12-30T12:00:05Z","tool":"fs.ls","args":{"path":".","why":"Survey workspace"}}
{"type":"tool_result","timestamp":"2025-12-30T12:00:05Z","tool":"fs.ls","success":true,"result":{"count":15}}
{"type":"model_output","timestamp":"2025-12-30T12:00:10Z","tokens":200}
```

---

## 5. Append-Only Guarantee

### Why Append-Only?

1. **Audit integrity** — History cannot be rewritten
2. **Debugging** — Full trace of what happened
3. **Replay** — Can reconstruct any past state
4. **Trust** — Users can verify agent behavior

### Enforcement

- Orchestrator MUST only append to events.jsonl
- Model CANNOT call `fs.write` or `fs.patch` on events.jsonl
- Any modification attempt is logged as a violation
- Corruption triggers recovery (backup + new file)

### Recovery from Corruption

```yaml
if events.jsonl corrupted:
  1. rename: events.jsonl → events.jsonl.corrupted
  2. create: events.jsonl (fresh)
  3. log: {"type":"recovery","from":"corruption","backup":"events.jsonl.corrupted"}
```

---

## 6. Querying Events

Events can be queried for analysis:

```python
# Example: Find all tool errors
grep '"type":"tool_error"' events.jsonl | jq .

# Example: Count tool calls by type
cat events.jsonl | jq -r 'select(.type=="tool_call") | .tool' | sort | uniq -c

# Example: Session duration
first=$(head -1 events.jsonl | jq -r .timestamp)
last=$(tail -1 events.jsonl | jq -r .timestamp)
```

### Useful Queries

| Query | Purpose |
|-------|---------|
| Tool call frequency | Performance analysis |
| Error patterns | Debugging |
| Context usage | Memory optimization |
| Turn duration | Latency tracking |
| Repair frequency | Health monitoring |

---

## 7. Event Retention

### During Session
- All events kept in `events.jsonl`
- No pruning during active session

### After Session
```yaml
retention_policy:
  hot: "keep indefinitely"    # Recent sessions
  warm: "compress after 7d"   # Older sessions  
  cold: "archive after 30d"   # Much older
  
compression:
  - Remove verbose results (keep summaries)
  - Aggregate repetitive events
  - Keep error and repair events
```

### Archival Format

```
.agent/archive/
  sessions/
    2025-12/
      sess-001.events.jsonl.gz
      sess-001.summary.yml
```

---

## 8. Cross-Session Events

Some events span sessions:

```jsonl
{"type":"cross_session_link","timestamp":"...","from_session":"sess-001","to_session":"sess-002","artifact":"shared_doc.md"}
{"type":"memory_import","timestamp":"...","from_session":"sess-001","imported":["decisions.md","glossary.md"]}
```

---

## 9. Event Aggregation

For analytics, events can be aggregated:

```yaml
# session_summary.yml (generated at session end)
session_id: "sess-001"
duration_minutes: 150
turns: 45

tool_usage:
  fs.read: 67
  fs.write: 23
  search.vector: 15
  terminal.run: 8
  
errors:
  total: 3
  by_code:
    NOT_FOUND: 2
    TIMEOUT: 1
    
repairs:
  total: 5
  by_demon:
    checklist_repairer: 2
    sticky_note_maintainer: 3
    
memory:
  peak_context_usage: 0.87
  gc_runs: 2
  summaries_created: 4
```

---

## 10. Privacy & Security

### Sensitive Data

Events MAY contain sensitive data. Handle appropriately:
- User messages logged (can be scrubbed)
- File contents NOT logged (only paths)
- Tool args logged (may need scrubbing)

### Scrubbing Policy

```yaml
scrub_before_export:
  - user_message.content
  - tool_call.args.password
  - tool_call.args.api_key
```

### Access Control

- Events readable by user and system
- Events not shared externally without consent
- Export requires explicit action

---

## 11. Dovetails With

- **Constitution** (§6): Audit requirements
- **Tool Calling Protocol**: Tool events
- **Memory Management**: GC events
- **Self-Healing Protocol**: Repair events
- **MOOLLM FlowMap Protocol (P-1.2)**: Data lineage

---

*Every action leaves a trace.*
*The trace is append-only.*
*The trace enables trust.*
