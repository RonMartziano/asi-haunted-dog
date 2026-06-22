# Asi The Haunted Dog — Complete Game Overview

A mobile-style, one-thumb **rogue-lite auto-battler** starring **Asi**, an adorable cream-colored pup who happens to be haunted by a demon. You send Asi forward through haunted chapters, he auto-fights, you make the interesting choices (which powers to take, when to **Unleash** the demon), and you grow stronger between runs with gear, talents, and the shop. It's built as a single self-contained HTML file with embedded pixel-art sprites, parallax backgrounds, and synthesized sound.

---

## 1. The hook & story

Asi was the happiest pup in the village — until the night of the **red moon**, when a shadow slipped beneath his skin. Now a demon sleeps in his bones, and when the battle-fury rises, it **wakes**. The tonal flip from "cutest dog ever" to "glowing, fanged engine of destruction" is the whole identity of the game.

**Story delivery is animated and in-engine:**
- A short **intro cutscene** plays on first launch — tap-through story beats over a forest scene, where Asi flips from his normal sprite to his ghostly green **haunted** sprite with a screen flash on the "the demon wakes" beat.
- A **new story beat returns after every 2 chapters cleared**, revealing more lore: the whisper that grows louder, a collar from a life Asi can't remember, the truth that the demon was once a guardian spirit bound to his bloodline, and the warning that every unleashing weakens the seal. Five story chapters exist so far.

---

## 2. The core loop

```
HOME (Adventure)  →  press ENTER CHAPTER
   → RUN: 10 encounters, auto-battle each one
       → land hits, build the HAUNT meter
       → on level-up, pick 1 of 3 POWERS
       → between fights, sometimes an EVENT (a choice)
       → choose when to UNLEASH the demon (burst)
   → ENCOUNTER 10 = BOSS
   → WIN → chapter rewards, advance to the next biome
   → (every 2 chapters: a story beat)
RETURN HOME → spend gold/gems/bones on gear, talents, shop
   → ENTER the next chapter, stronger
```

A run is ~10 quick encounters. The minute-to-minute job is **choices**, not reflexes — the fighting is automatic.

---

## 3. The Home / Adventure screen (what it looks like)

The home screen is the hub, with a **top currency bar** (🪙 gold, 💎 gems, 🦴 bones, hero level) and a **bottom tab bar**: 🏰 Adventure · 🎒 Gear · 🏪 Shop · ✨ Talents.

The **Adventure tab** is a framed "diorama":
- A **real parallax scene** as the backdrop (forest, graveyard, mountain, desert, or snow), tinted to match the current biome, with a soft vignette and drifting fog.
- **Asi animates live** here — he idles, walks around, and after sitting a while curls up to sleep, all using his real sprite frames.
- A **chapter banner** up top ("HAUNTED PARK / CHAPTER 1") with **difficulty stars** and a "▶ Next: Old Graveyard" chip. **Tapping the chapter title** opens a **rewards preview** popup showing exactly what clearing the chapter grants.
- A **live stat strip** (HP / ATK / DEF / Crit) plus your gear power and hero level.
- A big pulsing **▶ ENTER CHAPTER** button with a sheen animation.
- A 🏆 **Achievements** button in the corner.

**Feature unlocks are gradual:** Adventure and Gear are available from the start; **Talents and Shop unlock at Hero Level 2** (locked tabs show a 🔒 and tell you the level needed). This drips the systems in instead of dumping everything at once.

---

## 4. The Run / combat screen

When you enter a chapter the screen switches to the full-screen run view, split into two halves:

**Top half — the stage:** the parallax biome background, **Asi on the left**, the **enemy on the right**, HP bars and name plates above each, an encounter track ("Encounter 3 / 10") and a battle log. Asi plays his **idle / walk / attack** sprite animations; the lunge and the attack animation are timed to land together.

**Bottom half — the panel:** your **Level + XP bar**, a stat row, **active synergy chips**, the 👻 **HAUNT** meter, and your row of **acquired powers**.

**Per encounter:** Asi auto-attacks, the enemy counter-attacks, numbers float over the right person, and effects play **on the body** (not floating above). Combat has a few twists:
- **Enrage** — the longer a single fight drags on, the harder the enemy hits.
- **Status effects** — burn, poison (damage over time), freeze (a faceted ice-crystal overlay that stuns).
- **Defense is a curve, not a wall** — enemies always land a meaningful chunk, so high DEF can't make you invincible.

**Between encounters** Asi **walks forward** (his run animation) deeper into the biome, and you may hit a level-up or an event before the next fight.

**Enemy variety:** 12 biomes × 4 themed mobs each (~48 named enemies) plus bosses. About **1 in 6 non-boss fights spawns an ⭐ ELITE** — a golden, glowing enemy with ~+85% HP and +30% ATK that drops **double gold and a guaranteed gear piece**.

---

## 5. Powers, XP & synergies (in-run upgrades)

You earn **XP** from each kill. On **level-up** you pick **1 of 3 Power cards** (rarity-colored: Common → Legendary), shown in a polished pull-style picker. Powers stack across the run: raw stats (ATK/HP/DEF/Crit/Lifesteal), status chances (Burn/Freeze/Poison), and proc skills (Chain Lightning, Meteor, Smite, etc.). Effects fire **one at a time, ~1.5s apart** so you can actually read them.

**Power synergies** trigger automatically when you own the right pair, shown as a glowing chip and announced when completed:
- **Plague** (Burn + Poison) — +35% damage-over-time
- **Superconduct** (Freeze + Lightning) — lightning +60% vs frozen foes
- **Bloodfeast** (Crit + Lifesteal) — crits heal +6% HP
- **Cataclysm** (Meteor + Burn) — meteors set enemies ablaze

Run powers are **temporary** — they reset each run. Permanent power comes from gear and talents.

---

## 6. The Haunt meter & Demon Mode (the signature system)

Landing and taking hits fills the **Haunt meter**. When it's full, a pulsing **👹 UNLEASH** button appears over the stage and **you decide when to press it** — the one moment of agency in an otherwise auto-battle.

Unleashing triggers a **grand entrance**: a white→purple radial splash from Asi, an expanding shockwave ring, a big "👹 UNLEASHED" title, and a heavy screen shake. Asi swaps to his **haunted (ghostly green) sprite** with a demonic aura and gains **~2.4× ATK, +15% lifesteal, and crit frenzy**. The transformation now **persists for the next 2 combats**, then fades and the meter must be rebuilt. This is the natural home for the marketing hook, the story, and future monetization (longer/stronger demon, alternate demon forms).

---

## 7. Biomes & backgrounds (when they switch)

There are **12 biomes** — Haunted Park, Old Graveyard, Cursed Swamp, Hell's Gate, Molten Core, Frozen Waste, Storm Peaks, Bone Desert, Spirit Forest, Shadow Keep, Abyssal Deep, Cosmic Void. **Each chapter is a different biome**, so the background changes every time you advance a chapter (and cycles through the set as you go deeper). Visually each biome combines one of five **real parallax scene paintings** (mountain / desert / graveyard / snow / forest) with a per-biome **color tint and sky gradient**, so even biomes sharing a base scene look distinct. Each biome also has its own mob roster, boss, and accent color.

---

## 8. What happens when you WIN

**Per encounter win:** "CLEAR!" pops (with a combo counter), you collect gold and XP, heal a little (more in the early chapters), and Asi walks forward to the next fight.

**Clearing the chapter (beat the boss at encounter 10):** a **Chapter Complete** rewards screen grants a bundle that scales with the chapter — gold (≈chapter×40), gems (≈10 + chapter×3), bones, hero XP, and a **guaranteed gear drop** (gold-tier drops cap at Epic). Your **hero level** rises from the XP, the world **advances to the next chapter/biome**, and **every second chapter a story beat plays**. Then you're back home, richer, to gear up before the next run.

---

## 9. What happens when you LOSE

If Asi's HP hits zero mid-run, **"Asi has fallen…"** appears. If you have a **revive**, you can spend it to continue the run at 60% HP. Otherwise the run ends — but it's a **soft fail**: you **keep all the gold earned during the run, plus your gear, talents, gems and skins**. Only the temporary **run powers reset**. The message is "power up and try again," so losing always feeds back into permanent progression rather than punishing you. (Early chapters are tuned to be clearable with no shop or gear at all, so the wall comes later.)

---

## 10. Permanent progression (between runs)

**Gear / equipment.** Four slots (Collar, Charm, Claws, Cloak). Rarities run **Common → Rare → Epic → Legendary → Mythic (red)**. Crucially, **gold-based sources cap at Epic** — **Legendary and the ultra-rare Mythic only come from gem boxes**. There are **12 named unique Legendaries** (Fang of the Moon, Ragnarok Talons, Heart of the Abyss, Dragon's Shroud…) plus a deep affix pool (Ember, Vampiric, Berserker, Bulwark, Executioner…). Gear tiles are rarity-colored with glow and a 👑 badge on uniques. You **equip** from inventory and **recycle** unwanted gear into **scrap** to enhance keepers.

**Talents (permanent skill tree).** A 25-node tree spent with **🦴 bones**, organized into five branches labeled **PRECISION · MIGHT · CURSE · GUARD · FORTUNE**. Each node is gated two ways: a **row Hero-Level requirement** (Lv 1 / 2 / 4 / 7 / 11 / 16 / 22 by depth) **and** a tree prerequisite (**3–8 points in the node before it**). Locked nodes show whether they need a higher **🔒 Level** or more **🔒 points** in the parent. Talents give permanent stats and system-changers (Flurry double-strikes, Ember Lord DoT, Last Stand survival, Demon King unleash damage, Ascendant all-stats).

**Hero level.** Rises from chapter clears and idle rewards; it raises your base stats and unlocks features and talent rows.

**Skins.** Cosmetic forms (default Asi + others), each with a **haunted variant** used during Demon Mode. Bought with gems; purely a flex, never power.

---

## 11. The Shop

A clean, Capybara-Go-style shop with a currency header and four sub-tabs:
- **⭐ Featured** — the Weekly Hoard banner, Starter/Warrior value packs, a Free Gold timer, value packs, and a red **Relic Vault** card that points you to the gem boxes (the only place to get Legendary/Mythic gear).
- **📦 Chests** — four boxes with pity systems and glowing icon discs:
  - **Lesser Spirit Box** (cheap, gold) — **82% Common / 18% Rare**, perfect for farming scrap.
  - **Spirit Box** (gold) — Common→Epic.
  - **Demon Box** (gems) — Legendary 1%, Mythic 0.1%.
  - **Mythic Box** (gems) — Legendary 3%, Mythic 0.4%.
- **📅 Daily** — rotating daily deals.
- **🎭 Skins** — the cosmetic gallery.

**Currencies:** 🪙 Gold (battles/idle, soft currency), 💎 Gems (bosses, achievements, IAP-style premium), 🦴 Bones (talents), ⚙ Scrap (gear enhancement).

---

## 12. Live-service-style systems

- **Idle / AFK rewards.** While you're away (capped at 8 hours), Asi forages — on return a "Welcome Back" popup grants **gold, hero XP, and bones**, and even shows any levels gained offline.
- **Achievements.** A 🏆 panel with **12 milestones** (kills, bosses, elites, chapters reached, unleashes, gear found), each with a progress bar and a **gem reward** that auto-pays the moment you hit it.
- **Adventure events.** Roughly 40% of the gaps between fights spawn one of **13 branching events** — Campfire, Treasure Chest, Cursed Bones, Spirit Well, Demon Pact, Wandering Merchant, and more. The event arrives as a **glowing object on the path**: Asi walks up to it, you pick an option (risk/reward — heal, gold, a power, a curse), and then advance. Events are spaced out so you never get two back-to-back.

---

## 13. Feel & presentation

Everything is juiced: floating damage, crit pops, screen shake on the demon transform, particle auras, synthesized WebAudio sound effects (hits, procs, unleash, coins, victory, boss). UI uses a pixel display font (Thaleah) for titles and tabs. The whole game is **one self-contained HTML file** with all art and audio embedded, so it runs offline by double-clicking — and it's wired to **auto-deploy to GitHub Pages** so it's playable from a URL.

---

## 14. One-line summary

*You walk a haunted pup forward through cursed chapters, auto-battling and choosing powers; you decide when to unleash the demon inside him for a screen-shaking burst; you win gold, gems, bones and gear; you lose little; and between runs you build a permanent dog of mass destruction through gear, a talent tree, and a shop — all while a story slowly reveals how deep the haunting goes.*
