# MOOLLM Schemas
## Data Format Definitions

*Machine-readable definitions for MOOLLM data structures.*

---

## Purpose

These schemas define the format of key MOOLLM files:
- YAML structures for configuration
- JSON schemas for validation
- Documentation of required fields

---

## Schema Files

| File | Describes |
|------|-----------|
| `tool-schemas.yml` | Core tool input/output formats |
| `working-set-schema.yml` | Context assembly manifest |
| `meta-sidecar-schema.yml` | .meta.yml file format |
| `event-schema.yml` | Event log entry format |
| `instance-schema.yml` | Skill instance metadata |

---

## Usage

Schemas can be used for:
1. **Validation**: Check files conform to format
2. **Documentation**: Understand expected structure
3. **Generation**: Create compliant files
4. **Integration**: Build tools that work with MOOLLM

---

## Schema Format

Schemas use YAML with JSON Schema-compatible structure:

```yaml
$schema: "https://json-schema.org/draft/2020-12/schema"
$id: "moollm/schema-name"
type: object
properties:
  field_name:
    type: string
    description: "What this field means"
required:
  - field_name
```

---

**See also:**
- `../kernel/` — Protocols that use these schemas
- `../skills/` — Skills that produce these formats
