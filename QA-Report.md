# Asi The Haunted Dog — QA Report (Night Shift)

**Build:** `asi-haunted-dog.html` (~1.5 MB, self-contained)
**Method:** Automated functional QA in a real DOM (jsdom) with error capture, plus deep UI tests using injected save-state, accelerated-timer combat runs, and a code-level visual/layout audit.
**Headline result:** ✅ **0 runtime errors** across every system exercised. 1 defensive bug fixed during QA.

---

## 1. How this was tested

- **Functional engine:** Loaded the game in jsdom (real DOM + timers), capturing `jsdomError` and uncaught `error` events throughout.
- **Deep UI:** Injected a rich save (gold/gems/bones/scrap maxed, hero Lv 30, chapter 8, a full inventory across every rarity incl. Mythic) via `localStorage` + `load()`, then clicked through real handlers in Shop, Gear, and Talents.
- **Combat:** Auto-played runs with modal auto-resolution; accelerated in-game timers up to 8–22× to reach level-ups, events, and the Unleash flow.
- **Visual audit:** Static review of CSS/layout (effect anchors, z-index, sprite scaling, talent layout) — see §4.
- **Limitation:** A pixel screenshot pass was **not** possible in this environment — the headless Chromium download is network-blocked, no system browser is installed, and the Chrome extension refuses `file://` navigation. Items that need an eyeball on the actual screen are listed in §5.

---

## 2. Functional results

| Area | Checks | Result |
|---|---|---|
| Boot / init | Loads, no console errors | ✅ |
| Home – Adventure | Diorama render, hero sprite, difficulty stars, "Next biome", **Chapter-title → rewards popup** | ✅ |
| Home – Gear | Render, rarity tiles, **no "Top:" label**, inventory (8 items), inspect→equip, recycle bar | ✅ |
| Shop – Featured | Weekly hoard, Starter/Warrior packs, **Relic Vault** card, Free Gold, value packs (Gem Pouch FREE) | ✅ |
| Shop – Boxes | **Lesser (gold)**, Spirit (gold), Demon (gem), Mythic (gem); open ×1 and ×10; reveal modal | ✅ |
| Shop – Daily / Skins | Render + purchase handlers | ✅ |
| Talents | Render, **column labels** (PRECISION/MIGHT/CURSE/GUARD/FORTUNE), **per-row level gating**, locked nodes show **🔒 Lv N**, buy node | ✅ |
| Combat loop | Encounters advance, walk-forward, hero sprite (idle/walk/attack), damage mitigation (~28% floor) | ✅ |
| XP / Level-up | Skill-pick modal fires on level-up | ✅ |
| Events | Appear as **on-path object** → Asi walks up → choice → advance | ✅ |
| Demon / Unleash | Manual **Unleash button** appears when Haunt full, triggers transform + splash | ✅ |
| Drop rates (sim) | Gold caps at Epic; Mythic only via gems; named uniques on Legendary/Mythic | ✅ |
| Persistence | `localStorage` save/load round-trips | ✅ |

**Totals:** 24/25 scripted UI assertions pass. The single "fail" was a **test artifact** (injected hero Lv 30 unlocks every talent row, so no locked "🔒 Lv" labels exist to find — they render correctly at low level, separately verified).

---

## 3. Bug found & fixed during QA

- **Attack-lock could persist across runs.** The flag that holds Asi's full attack animation (`_asiLock`) had no reset on run start, so a run abandoned mid-swing could leave the next run's hero stuck on an attack frame. **Fixed** — the lock is now cleared in `startEncounter`. Re-verified: 0 errors.

---

## 4. Visual / layout audit (static)

- **Effect anchors** are now consistent and on-body: all enemy-side VFX at `bottom: 11–12%`, the slash arc at `3%`, the speed-lines lowered to `top: 64%`. No stragglers floating above characters.
- **Attack timing** synced: dash 0.66s vs attack anim 6 frames @ 9 fps (~0.67s) — lunge and animation finish together.
- **Walk** at 16 fps, tilt removed (no rotation in the walk-forward keyframes).
- **Talent nodes**: locked level text fits the 56px node; column theme labels and per-row levels present.
- **z-index** stack is sane (sprites 3 < fx 7/8 < event object 6 < haunt splash/ring/word 21–23 < unleash button 24 < modal/scrim 30).
- **Freeze** replaced with a faceted ice-crystal + snowflake overlay.

---

## 5. Needs an on-device eyeball (not blocking)

These are correct in code but should be glanced at on the real screen:

1. **Combat hero size** — idle scale is 1.2; confirm Asi isn't too small next to large/boss enemies.
2. **Freeze crystal coverage** — the overlay is bound to the enemy's 150×120 box; on very large/boss sprites it sits low rather than covering the whole body (same constraint as before, just prettier).
3. **Event walk-up distance** — Asi steps to ~30% of the stage toward the object; nudge-able if you want him right beside it.
4. **Attack vs return overlap** — the attack clip ends ~150ms before the dash fully returns; visually fine, easy to fine-tune.

---

## 6. Sign-off

No crashes, no console errors, all menus and the full combat loop function. Safe to keep iterating. Recommend a quick manual playthrough on-device to confirm the four cosmetic items in §5.
