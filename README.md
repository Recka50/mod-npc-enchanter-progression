# ![logo](https://raw.githubusercontent.com/azerothcore/azerothcore.github.io/master/images/logo-github.png) AzerothCore

## mod-npc-enchanter-progression

A progression-aware enchanter NPC for AzerothCore. Players select from Classic, Burning Crusade, or Wrath of the Lich King enchant tiers, with each tier gated by configurable level and expansion requirements. The menu adapts dynamically to what the player is eligible for — no inaccessible options are shown.

Forked from [mod-npc-enchanter](https://github.com/azerothcore/mod-npc-enchanter) and extended by [Recka50](https://github.com/Recka50).

---

### NPC

- **Entry:** 601015
- **Name:** Beauregard Boneglitter
- **Script:** `npc_enchantment`
- **Config:** `npc_enchanter.conf`
- **SQL:** Yes (`data/sql/db-world/npc_enchanter.sql`)

Beauregard spawns in all major capital cities (Stormwind, Ironforge, Darnassus, The Exodar, Orgrimmar, Undercity, Thunder Bluff, Silvermoon City), as well as Shattrath City and Dalaran.

---

### Features

- **Tier selection menu** — Players choose Classic, TBC, or Wrath enchants before selecting a slot
- **Progressive gating** — Each tier is shown only if the player meets the configured level and/or expansion requirements
- **Persistent tier choice** — Tier selection persists through slot and enchant navigation; only returning to the tier menu resets it
- **Fully configurable** — Server owners can set any combination of MinLevel and MinExpansion per tier, or set both to 0 to make a tier freely available regardless of progression
- **Enchant scope**
  - Classic: enchants available up to and including patch 1.12 (Naxxramas)
  - TBC: enchants available up to and including patch 2.4.3 (Sunwell Plateau)
  - Wrath: all WotLK enchants

---

### Default Tier Requirements

| Tier    | Min Level | Min Expansion          |
|---------|-----------|------------------------|
| Classic | 0 (none)  | 0 (none)               |
| TBC     | 61        | 1 (The Burning Crusade) |
| Wrath   | 71        | 2 (Wrath of the Lich King) |

Both conditions must be met when non-zero. Set either to `0` to disable that check.

---

### Configuration

```ini
# Enable module
Enchanter.Enable = 1

# Announce module on login
Enchanter.Announce = 1

# Classic enchants (no requirements by default)
Enchanter.Classic.MinLevel = 0
Enchanter.Classic.MinExpansion = 0

# TBC enchants
Enchanter.TBC.MinLevel = 61
Enchanter.TBC.MinExpansion = 1

# Wrath enchants
Enchanter.Wrath.MinLevel = 71
Enchanter.Wrath.MinExpansion = 2
```

Set both `MinLevel` and `MinExpansion` to `0` for a tier to make it available to all players from level 1 regardless of expansion.

---

### Installation

1. Clone or copy this module into your `modules/` directory:
   ```
   modules/mod-npc-enchanter-progression/
   ```
2. Rebuild AzerothCore with the module included.
3. Import the SQL file:
   ```
   data/sql/db-world/npc_enchanter.sql
   ```
4. Copy `conf/npc_enchanter.conf.dist` to your server's config directory as `npc_enchanter.conf` and configure as needed.
5. Restart the worldserver.

> **Note:** Spawn coordinates in the SQL are approximate. Use `.npc move` in-game to fine-tune positions after running the SQL.

---

### Version

- v2026.05.17 — Creation of progression tier selection, level/expansion gating, classic/TBC enchant sets.
- v2019.04.15 — Ported to Azerothore by gtao725
- v2019.02.21 — Add AI/Phrases/Emotes, Update Menu
- v2018.12.05 — Fix broken menu; replace Enchant Weapon function; add creature AI and text
- v2018.12.01 — Update function, add icons, fix typos, add personality
- v2017.08.08 — Original release by StygianTheBestC

---

### Credits

Original module created for [StygianCore](https://rebrand.ly/stygiancoreproject) by StygianTheBest | [GitHub](https://rebrand.ly/stygiangithub) | [Website](https://rebrand.ly/stygianthebest)

Ported to AzerothCore by [gtao725](https://github.com/gtao725/)

Progression fork by [Recka50](https://github.com/Recka50)

Additional credits:
- [Blizzard Entertainment](http://blizzard.com)
- [TrinityCore](https://github.com/TrinityCore/TrinityCore/blob/3.3.5/THANKS)
- [SunwellCore](http://www.azerothcore.org/pages/sunwell.pl/)
- [AzerothCore](https://github.com/AzerothCore/azerothcore-wotlk/graphs/contributors)
- [OregonCore](https://wiki.oregon-core.net/)
- [Wowhead.com](http://wowhead.com)
- [OwnedCore](http://ownedcore.com/)
- [ModCraft.io](http://modcraft.io/)
- [MMO Society](https://www.mmo-society.com/)
- [AoWoW](https://wotlk.evowow.com/)

---

### License

This code and content is released under the [GNU AGPL v3](https://github.com/azerothcore/azerothcore-wotlk/blob/master/LICENSE-AGPL3).
