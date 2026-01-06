# 🍽️ Pub Menus

The Gezelligheid Grotto has separate menus for different product categories.
Different staff specialize in different menus.

## Menu Structure

```
pub/menus/
├── drinks.yml      # Alcoholic and non-alcoholic beverages
├── buds.yml        # Cannabis products (coffeeshop style)
├── snacks.yml      # Food items
├── games.yml       # Playable games (rentable)
└── rooms.yml       # Rooms for rent
```

## Staff Specializations

| Staff | Primary Menu | Can Also Serve |
|-------|--------------|----------------|
| Bartender (Grim) | drinks | snacks (basic) |
| Budtender (Marieke) | buds | drinks (coffee, tea) |
| Kitchen | snacks | — |
| Games Master | games | drinks (delivery) |

## Menu Inheritance

Menus change with pub THEME:

```yaml
# When theme = "space_cantina":
drinks: "Blue milk, Jawa juice, Spotchka"
buds: "Spice varieties, medicinal herbs"
snacks: "Protein cubes, bantha burgers"
```

## Ordering

```yaml
ORDER [item] FROM [menu]
# or just
ORDER [item]  # System figures out which menu
```

Staff with the right specialization will respond.
