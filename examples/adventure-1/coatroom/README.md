# The Coat Room

> *"Be anyone you want!"*
> — The Fantastipants Costume Emporium

A vast circular chamber of infinite costume possibilities. Transform yourself completely!

**Inspired by The Sims' Create-a-Sim screen** — and appropriately located right near the entrance! Just like starting a new Sims game, you can customize your character before the adventure begins. Change your appearance, add accessories, mix and match personas. The adventure awaits, but first: *who do you want to be?*

**Also an NPC factory!** Generate new characters, dress them up, accessorize them, and dispatch them into the world. Need a rival adventurer? A helpful guide? A suspicious merchant? Create them here, costume them, give them inventory, and send them off to populate your adventure.

---

## How It Works

The coat room rewrites your **character description** based on what you wear. Your costume persists throughout the adventure!

### Commands

| Command | Effect |
|---------|--------|
| `WEAR [description]` | Become that costume! |
| `WEAR RANDOM` | Surprise costume! |
| `COMBINE [a] WITH [b]` | Mash-up two costumes! |
| `ADD [accessory]` | Add to current costume |
| `ADD TO INVENTORY [item]` | Get a costume-appropriate item |
| `REMOVE COSTUME` | Back to default Bumblewick |
| `LOOK IN MIRROR` | See your current appearance |

---

## Examples

**Simple:**
```
> WEAR pirate captain

You are now Captain Bumblewick "Blackwaistcoat" Fantastipants!
Tricorn hat, brass buttons, foam cutlass, and a parrot puppet
that squawks unconvincingly.
```

**Combination:**
```
> COMBINE astronaut WITH Victorian gentleman

You emerge as Space Explorer Sir Bumblewick Fantastipants III,
in a silver spacesuit with a top hat sealed to the helmet and
a monocle painted on the visor.
```

**Custom:**
```
> WEAR a sentient cloud of bees wearing a tiny crown

The mannequin nods approvingly. Somehow, this exists.
You are now... The Bee Emperor. Buzz buzz.
```

**Add accessories:**
```
> ADD a jetpack

Your costume now includes a jetpack! (Decorative only. 
Or is it? Try pressing the button in the maze...)

> ADD TO INVENTORY rubber chicken

You now have: Rubber Chicken (squeaks when squeezed)
```

---

## Featured Costumes

| Costume | Description |
|---------|-------------|
| **Dread Pirate** | Tricorn hat, cutlass, parrot puppet |
| **Space Explorer** | Silver suit, ray gun, bubble helmet |
| **Detective** | Upgraded waistcoat, deerstalker, magnifying glass |
| **Three Corgis** | Trenchcoat, tiny hat, surprisingly convincing |

---

## Categories Available

- **Historical**: Roman, Egyptian, Victorian, 1920s...
- **Fantastical**: Wizard, fairy, dragon, superhero...
- **Professional**: Chef, astronaut, detective, scientist...
- **Theatrical**: Harlequin, Phantom, Shakespeare...
- **Absurdist**: Banana, hotdog, "concept of time"...
- **Custom**: If you can describe it, you can wear it!

---

## The Objects

| Object | What It Does |
|--------|--------------|
| **[mirror.yml](./mirror.yml)** | Shows your current appearance |
| **[mannequin.yml](./mannequin.yml)** | Helps you choose, handles RANDOM |
| **[costume-racks.yml](./costume-racks.yml)** | The infinite collection |

---

## Why Costumes?

- **Roleplay differently** through the adventure
- **Get into character** for puzzles and challenges
- **Add inventory items** that match your persona
- **Learn skills!** Using the costume racks teaches `costume-combining`
- **Have fun!** The maze is scary. Costumes are fun.

## Skills You Can Learn Here

Interacting with objects in the coatroom can teach persistent skills:

| Interaction | Skill Learned | Carries To |
|-------------|---------------|------------|
| `COMBINE` costumes | `costume-combining` | Any room with costumes |
| `WEAR RANDOM` repeatedly | `style-improvisation` | Social encounters |
| Help the mannequin | `fashion-consulting` | NPC interactions |
| `ADD TO INVENTORY` | `accessorizing` | Equipment management |

These skills persist in your `player.yml` and travel with you!

---

## Navigation

| Direction | Destination |
|-----------|-------------|
| 🚪 West | [start/](../start/) — Chamber of Commencement |
| 🍳 (via start) | [kitchen/](../kitchen/) — Food for maze mapping |
| 🌀 (via start) | [maze/](../maze/) — The grue-infested maze |
| ⬆️ Up | [adventure-1/](../) |
