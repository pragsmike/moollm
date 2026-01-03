# Examples

> *"Show, don't tell. Then tell what you showed."*

Each example directory captures:
1. **The chat dialog** that created it (this README)
2. **The artifacts** produced (YAML files, rooms, characters)
3. **How to explore** the example yourself

---

## How Examples Work

Examples are **live adventures** you can explore and modify. Each one was created through conversation — the README documents what we said to create it.

```
examples/
├── README.md              # This file
├── adventure-1/           # First adventure: two rooms
│   ├── README.md          # Chat log that created it
│   ├── player.yml         # The hero
│   ├── start/             # Starting room
│   │   └── ROOM.yml
│   └── end/               # Destination room
│       └── ROOM.yml
└── [more examples...]
```

---

## The Examples

| Example | Description | Complexity |
|---------|-------------|------------|
| [adventure-1/](./adventure-1/) | Two rooms, one hero — the minimal adventure | ⭐ Beginner |

---

## Creating New Examples

Every example starts with a conversation:

```
User: "Create an adventure with X, Y, Z..."
DM: [creates files, explains structure]
User: "Now add W..."
DM: [extends, documents]
```

The README in each example IS that conversation — a tutorial and history in one.

---

## Dovetails With

| Resource | Relationship |
|----------|--------------|
| [skills/adventure/](../skills/adventure/) | The adventure protocol these examples implement |
| [skills/room/](../skills/room/) | Room structure and navigation |
| [skills/card/](../skills/card/) | Characters and objects as cards |
| [PROTOCOLS.yml](../PROTOCOLS.yml) | Symbol definitions |

---

## Navigation

| Direction | Destination |
|-----------|-------------|
| ⬆️ Up | [Project Root](../) |
| 📖 Skills | [skills/](../skills/) |
| 🎯 Adventure Protocol | [skills/adventure/](../skills/adventure/) |
