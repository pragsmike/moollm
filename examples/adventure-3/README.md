# 🎮 Adventure 3: A New Hero Awakens

> *The paint is dry on adventure-2. The world has been shaped by legend.*  
> *Now it's YOUR turn.*

---

## 🌍 The World State

This adventure inherits the **enriched world** from adventure-2, where Bumblewick Fantastipants became Captain Ashford and slew a grue with blue cheese.

### What's Preserved (World Improvements)

| Feature | Description | Location |
|---------|-------------|----------|
| 🏛️ **Initials on the Wall** | WC+DW '76, SA '78, CA '26, BF — the lineage | `start/ROOM.yml` |
| ⬆️ **Stairway to Home** | Exit UP leads to the surface | `start/` → `home/` |
| 🎭 **Maurice's Skills** | Learned PHOTO-SET-8 in adventure-2 | `coatroom/mannequin.yml` |
| 🏪 **Vending Machine** | Sells Premium Glow Juice | `maze/room-j/lamp-vendor.yml` |
| 💀 **The Skeleton** | Still points west, still waiting | `maze/room-i/ROOM.yml` |
| 💰 **100 Gold Pile** | In the grue's lair | `maze/room-f/gold-pile.yml` |
| 📖 **Legends** | Tales of the Grue Slayer | Throughout |

### What's Reset (Fresh Start)

| Feature | State | Notes |
|---------|-------|-------|
| 🧑 **Player** | New unknown hero | Identity to be discovered |
| 🪔 **Lamp** | Full (100 oil) | On the shelf, waiting |
| 🧊 **Fridge** | Fully restocked | 20 food items |
| 📓 **Notebook** | Empty | Your story awaits |
| 🍱 **Lunchbox** | Empty | In the kitchen |
| 💰 **Starting Gold** | 10 | Enough for lamp refills |
| 🐉 **The Grue** | RESPAWNED | Grues always respawn |
| 🗺️ **Maze Markers** | Cleared | Map it yourself! |

---

## 🎯 Your Goals

From Mother's note on the kitchen table:

1. **Find treasure** (+10 points)
2. **Bring gold home** (Mother's approval)
3. **Return home safely** (Adventure complete!)

*Plus eight promises to keep... but you'll find those yourself.*

---

## 🗺️ The World

```
                              HOME
                               ↑ up
                               │
    ┌──────────────────────────┼──────────────────────────┐
    │                          │                          │
    │                    ╔═════╧═════╗                    │
    │                    ║   START   ║                    │
    │                    ║  Chamber  ║                    │
    │                    ╚═════╤═════╝                    │
    │                          │                          │
    │    COATROOM ←── east ────┼──── west ──→ KITCHEN     │
    │    (Maurice)             │              (Fridge)    │
    │                          │ north                    │
    │                          ↓                          │
    │                    ╔═══════════╗                    │
    │                    ║   MAZE    ║                    │
    │                    ║ 10 rooms  ║                    │
    │                    ║  (DARK!)  ║                    │
    │                    ╚═════╤═════╝                    │
    │                          │                          │
    │                          ↓                          │
    │                    ╔═══════════╗                    │
    │                    ║  TREASURY ║                    │
    │                    ║ (treasure)║                    │
    │                    ╚═══════════╝                    │
    │                                                     │
    └─────────────────────────────────────────────────────┘
```

---

## 🎬 Begin Your Adventure

**Move 0: Awakening**

You stir. The Chamber of Commencement. Carved initials on the walls tell of those who came before. A brass lamp waits on a shelf.

> `GET LAMP`

*Your story begins...*

---

## 📜 Chat Log

*This space will fill with your adventure as you play.*

---

### Move 1: ???

**User:** `[your first command]`

**DM:** *[what happens...]*

---

## 📊 Current State

```yaml
player:
  name: "Unknown Hero"
  location: start/
  moves: 0
  score: 0
  gold: 10
  
inventory: []
  # GET LAMP!
  
goals:
  - Find treasure: PENDING
  - Bring gold home: PENDING  
  - Return home safely: PENDING
```

---

## 🧬 Lineage

| Adventure | Hero | Achievement |
|-----------|------|-------------|
| 1 | *(template)* | World created |
| 2 | **Captain Ashford** (Bumblewick) | Slew grue with cheese, 8/8 promises, PhD paper |
| 3 | **???** | *Your story here* |

---

## 🎭 Tips for New Adventurers

1. **GET LAMP** — In the start room. Don't enter the maze without it.

2. **Visit the Kitchen** — Everything you need is on the table:
   - 📜 **Mother's Note** — Important instructions and love
   - 🧭 **TomTomagotchi** — Your navigation pet (GPS + friend!)
   - 📓 **Notebook** — For collecting memories (auto-sorts!)
   - 🍱 **Lunchbox** — For carrying food

3. **⭐ READ THE NOTE. WRITE A REPLY. MAKE PROMISES!** ⭐
   
   > *This is the most important step for a rich adventure!*
   
   Mother's note asks you to be careful. **Write back to her!**
   - Who are you today? What costume will you wear?
   - What do you promise to bring home?
   - What do you promise NOT to do?
   - What questions do you have?
   - What do you want to tell her?
   
   **Your promises become YOUR GOALS.** The DM tracks them. At the end
   of the adventure, you'll discover which promises you kept — and which
   you broke. Mother will have opinions.
   
   *This is freeform creative writing that creates game mechanics!*

4. **Raid the Fridge** — 20 food items for maze mapping.
5. **Visit the Coatroom** — Maurice can help you discover who you want to be.
6. **The Grue Has Respawned** — It's hungry. It's waiting. It's in room-f.
7. **The Vending Machine** — Room J sells Premium Glow Juice (3 gold).
8. **The Skeleton Points West** — Follow its guidance.
9. **There's 100 Gold** — In the grue's lair. If you dare.

---

## ✨ What's New in Adventure 3

*The Fantastipants Kitchen has been... upgraded.*

### 🔧 The Workbench

That old granite counter? It's more than meets the eye. Mother always said it "tingled" — turns out she wasn't exaggerating.

**What can you do there?**
- **COMBINE** things to make new things
- **TRANSFORM** things into different things  
- **EDIT** things to change their properties
- **PROGRAM** things to do things when other things happen
- And something else... something that goes *deeper*...

Every experiment you succeed at? The counter remembers. It *learns*.

### 📦 Mail-Order... Something

There's a catalog on the counter. Dog-eared. The coyote on the cover looks optimistic.

> *"ORDER ANYTHING! DELIVERED IN 2-4 TURNS!"*
> *"Satisfaction Guaranteed!*"*

The asterisk leads to very small print.

Items ordered from this catalog *work*. Technically. Usually. The malfunction rate is only... well, Tom has calculated it. Tom has concerns.

### 🗄️ The Drawers

Three drawers under the counter. Father's motto: *"You never know what you'll need."* Mother's motto: *"Why do we have SEVEN broken compasses?"*

One of those compasses might be interesting. Tom keeps looking at it.

### 🗑️ The Trash Can

Don't ask where it leads. Don't climb in unless you're prepared.

If you do... well. Your hair will be *fabulous* when you return.

### 📋 Family Recipes

Some recipes are for sandwiches. Some are for soup.

One requires you to slay a monster with dairy products.

Another is too stained to read. *Experiment.*

### 🧪 Going Deeper

The counter can break things down. Not just "disassemble" — *decompose*.

- Kitchen-level? Easy. Sandwich → bread + cheese.
- Chemical-level? Sure. Water → hydrogen + oxygen. (Store in jars.)
- Atomic-level? The counter starts humming.
- Subatomic-level? The room vibrates. Reality wobbles.
- Philosophical-level? **Do not decompose meaning. You need it.**

*See also:*
- *[How to Deconstruct Almost Anything](http://www.fudco.com/chip/deconstr.html) — Chip Morningstar's legendary essay on the collision of engineering and postmodern literary criticism.*
- *[Captain Ashford's Deconstruction Paper](../adventure-2/kitchen/postmodern-deconstruction.md) — Our own PhD-level analysis of adventure-2, applying Morningstar's methods to grues, lamps, and the filesystem-as-world.*

*If you're going to decompose reality, you might as well understand the theory.*

Components can be recombined. Hydrogen + oxygen = water (and a small boom). What else might you synthesize?

---

## 🧪 Emergent Mechanics (from adventure-2)

*Patterns discovered through play. Use as inspiration!*

| Mechanic | What Happens | See |
|----------|--------------|-----|
| 🧭 **TomTomagotchi** | Navigation pet that grows with your adventure | [kitchen/tomtomagotchi.yml](./kitchen/tomtomagotchi.yml) |
| 👃 **Smell Gradients** | Transformed food emits smells that diffuse through rooms | [maze/README.md](./maze/README.md) |
| 🔮 **Object Transformation** | Eaten food becomes sentient, prophetic, weaponized... | [kitchen/fridge.yml](./kitchen/fridge.yml) |
| 🐉 **Grue Personality** | The grue can speak, bargain, fight, be eaten | [maze/room-f/](./maze/room-f/) |
| 💀 **Skeleton Stories** | The skeleton accepts gifts, memorials, visitors | [maze/room-i/](./maze/room-i/) |
| ⚡ **Speed of Light** | DM simulates multiple moves seamlessly | [maze/README.md](./maze/README.md) |
| 🎭 **Identity Play** | Costumes affect transformations and interactions | [coatroom/](./coatroom/) |

**DM Principle:** These are EXAMPLES that suggest possibilities. Defer creativity until runtime. Improvise. Surprise yourself!

---

## 📚 References

- [adventure-2/README.md](../adventure-2/README.md) — The legend of Captain Ashford
- [coatroom/mannequin.yml](./coatroom/mannequin.yml) — Maurice and PHOTO-SET-8
- [kitchen/fridge.yml](./kitchen/fridge.yml) — The EAT mechanic
- [maze/room-f/](./maze/room-f/) — The grue's lair
- [maze/room-j/lamp-vendor.yml](./maze/room-j/lamp-vendor.yml) — Premium upgrades

---

*Adventure 3 forked from adventure-2 on January 4, 2026*

*The world remembers. The grue waits. What will YOU do?*
