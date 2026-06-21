# Asi The Haunted Dog — Game Design Document

**Version:** 0.1 (vertical-slice prototype)
**Date:** June 2026
**Genre:** Rogue-lite auto-battle adventure RPG (idle-casual)
**Platform:** Mobile-first (iOS / Android), portrait orientation
**Reference DNA:** Capybara Go (core loop), Wittle Defender (squad/roguelite picks), AFK Arena (meta progression & monetization)

---

## 1. One-line pitch

You adventure forward with **Asi**, an adorable fluffy dog — but a demon haunts him. Fill the **Haunt Meter** in battle and **unleash Demon Mode**, turning sweet Asi into a glowing, fanged engine of destruction. Run, fight, grow stronger, and see how deep the curse goes.

## 2. Design goals

- **Cute-meets-cursed hook.** The tonal flip from adorable to demonic is the marketing and retention hook. Every session should deliver at least one satisfying transformation.
- **Low-friction, high-reward.** Auto-battle by default. The player's job is *choices*, not reflexes — exactly the Capybara Go promise.
- **Always something to chase.** Stage progress, level-ups, gear, meta currencies, and the Haunt/Demon system layer so there's never a dead minute.
- **Snackable but deep.** 60-second loops that compound into long-term builds.

## 3. Core loop (the 60-second heartbeat)

```
ADVANCE a stage  →  AUTO-BATTLE  →  build HAUNT  →  UNLEASH DEMON (burst)
      →  WIN  →  collect Gold/XP  →  LEVEL UP? pick 1 of 3 POWERS
      →  every 4 stages: ADVENTURE EVENT (branching choice)
      →  every 10 stages: BOSS  →  repeat
```

This mirrors Capybara Go's "tap the next day, things happen automatically, occasionally make a roguelike 3-choice decision" rhythm, with the Demon Mode as our signature active beat layered on top of an otherwise idle flow.

## 4. The signature system — Haunt & Demon Mode

The differentiator versus every capybara/animal-runner clone.

**Haunt Meter (0–100).** Fills passively during battle:
- +6 per hit Asi *lands*
- +8 per hit Asi *takes* (suffering feeds the demon — encourages risk)
- Modifiers: "Restless Spirit" upgrade builds it +40% faster; some events add flat Haunt.

**Unleash (player-triggered).** When full, an **UNLEASH DEMON** button pulses. Tapping it:
- Transforms Asi → **Haunted Asi** (art swap, screen shake, purple flash, growl SFX).
- Grants for **5 turns** (extendable): **ATK ×1.8**, **+12% lifesteal**, crit frenzy.
- Drains the meter to 0; it must be rebuilt.

**Why it works:** it's a manual power spike inside an idle game — the one moment of agency that makes auto-battle feel like *yours*. It's also the natural home for monetization and progression (longer demon, stronger demon, auto-unleash, second demon form).

**Live in the prototype:** fully implemented and tuned — demon hits land ~3.5× a normal hit in testing.

## 5. Progression systems

| System | What it does | Reference |
|---|---|---|
| **Stage advance** | Linear chapters/stages, each unlocks the next. Bosses every 10. | Capybara Go |
| **Hero level (XP)** | Battles grant XP. On level-up, pick **1 of 3 Power cards** (rogue-lite). | Wittle Defender / Capybara Go |
| **Powers (run upgrades)** | Stat boosts + system-changers (lifesteal, haunt rate, deeper curse). Rarity tiers Common/Rare/Epic. | Wittle Defender cards |
| **Gear / relics** *(planned)* | Equippable items with stats + set bonuses; drop from bosses. | AFK Arena equipment |
| **Adventure events** | Every 4 stages, a branching choice (risk/reward, shop, shrine). | Capybara Go events |
| **Meta currencies** | Gold (in-run upgrades/shop), Gems (premium: summons, revives). | AFK Arena |
| **Idle / AFK rewards** *(planned)* | Offline accrual of gold/XP; "claim" on return. Core retention driver. | AFK Arena |

## 6. Economy & currencies

- **Gold (🪙):** soft currency. Earned every battle; spent on upgrades, gear rolls, shop. Generous faucet.
- **Gems (💎):** hard currency. From bosses, milestones, IAP. Spent on summons, revives, demon-skin cosmetics.
- **Haunt:** in-battle resource (not bankable), the Demon Mode fuel.
- **Faucets:** battle wins, bosses (×3 gold + gems), events, idle accrual, daily login.
- **Sinks:** power rerolls, gear gacha, revives, cosmetic demon skins, stamina refills *(if added)*.

**Balance philosophy:** keep early stages a fast dopamine ramp (player feels strong), then introduce **boss walls** (stage 10/20/30) where the player must spend meta progression — gear, idle gold, or a well-timed Demon Mode — to break through. The prototype's curve already creates these walls (boss HP jumps ~5–6× a normal enemy).

## 7. Monetization (free-to-play)

Modeled on AFK Arena's "monetize *progression*, not *content*" approach:

1. **Battle Pass / season track** — cosmetic demon skins + currency, the healthy backbone.
2. **Summon gacha** — heroes/companions or gear, with a **pity/wishlist** system (AFK Arena's guaranteed-after-N mechanic) to avoid bad-luck churn.
3. **VIP / subscription** — faster idle accrual, extra fast-rewards, auto-unleash demon.
4. **Convenience IAP** — revives, idle-time skips, stamina.
5. **Demon cosmetics** — alternate demon forms (frost demon, ember demon). Pure flex, high margin, on-brand.

*Avoid:* energy gates harsh enough to block the cute-hook early; that kills the viral first session.

## 8. Retention & engagement

- **Daily:** login reward, daily bounties, AFK chest, one free summon.
- **Weekly:** boss rush, event dungeon, season milestones.
- **Push-worthy moments:** "Asi's Haunt is overflowing," "AFK rewards full," "New demon form unlocked."
- **Social hooks (later):** guilds, co-op boss, friend leaderboards (best stage).

## 9. UX / flow

- **One-thumb, portrait.** Everything reachable bottom-half of screen.
- **Auto-battle default**, with a visible AUTO toggle and (planned) 2×/3× speed.
- **Modal choices** (powers, events) pause the flow — the only times the player *must* decide.
- **Juice:** floating damage, crit pops, screen shake on transform, particle aura. This is in the prototype.

## 10. Art direction

See the companion **Art & Vibe Board**. Pillars: cute-meets-cursed, moonlit dread (purples/void/embers), juicy feedback. Asi's real traits preserved — cream coat, feathered ears, happy tongue, plumed tail; demon-mode horns nod to his flower-crown photo. Next art step: full sprite sheets (idle / attack / transform / hit / victory) for both forms.

## 11. Tech recommendation

**Prototype & soft-launch:** **Phaser 3 (HTML5/TypeScript)** → wrap to native iOS/Android with **Capacitor**.
- *Why:* instant iteration, runs in any browser today, one codebase to mobile, ideal for proving the loop cheaply. The included prototype is already a real Phaser game, not a static page.

**If/when it scales:** migrate to **Unity** (what Capybara Go and most of this genre ship on) for richer Spine animation, mature ad/IAP SDKs, and live-ops tooling. Decision gate: prove D1/D7 retention and the demon-hook in Phaser first, then port.

## 12. Prototype status (what's built & playable)

Implemented in `asi-haunted-dog-prototype.html`:
- ✅ Auto-battle core loop with turn-based strikes, HP bars, juice
- ✅ **Haunt Meter → Demon Mode** transformation (art swap, FX, buff, duration)
- ✅ Stage progression + bosses every 10 stages with scaled difficulty
- ✅ Level-up **rogue-lite 1-of-3 Power picks** (8 powers, 3 rarities)
- ✅ **Adventure events** every 4 stages with branching choices
- ✅ Gold / Gems / XP economy, soft-fail (retreat) on defeat
- ✅ Local save/persistence, AUTO toggle, reset

**Not yet (next sprint):** gear/relics, idle/AFK accrual, summon gacha + pity, multiple demon forms, sound, sprite-sheet animation, server save.

## 13. Roadmap (suggested)

- **Sprint 1 (done):** playable core loop + demon mechanic + art direction. ← *you are here*
- **Sprint 2:** gear/relics, idle rewards, daily login, sound pass.
- **Sprint 3:** summon gacha + pity, second demon form, juice/polish, soft-launch build via Capacitor.
- **Sprint 4:** live-ops scaffolding (season pass), analytics, retention tuning → soft launch in 1–2 test geos.

---

*Companion files: `asi-haunted-dog-prototype.html` (playable), `asi-art-vibe-board.html` (art direction).*
