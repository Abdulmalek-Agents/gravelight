# 📜 Game Design Document — Gravelight

> **GDD v1.1** — approved by Creative Director after 14-expert Cycle 2 review (12/14 clean, 2 approved-with-notes, 3 required changes applied).

## 1. High-concept

You are **Wren**, a young necromancer apprenticed to your late grandmother. You've inherited her duty: tending the **Old Yard**, a sprawling Victorian graveyard whose dead have grown restless since she died. You are kind. You are good with plants. The dead remember her, and they listen to you. By **day** you garden, mend headstones, plant moonflowers, and listen to mourners. By **night** the restless dead rise — and you must use your **grave-lantern** to guide the gentle ones to peace and reap the violent ones into your obedient necro-army.

**Player fantasy:** *I am the gentle necromancer who reads the dead's needs and gives them light.*

**Emotional journey:** Trepidation (first night) → competence (first soul reaped) → community (the mourners trust you) → power (your necro-army marches with you) → catharsis (the Pale Reaper, and your grandmother's choice).

**Pillars (do not violate):**
1. **Cozy palette, never grimdark.** Lavender, moss, gold lantern, soft bone-white.
2. **The dead are people.** Not all souls are enemies. Some you guide; some you reap; some you must let pass.
3. **Day-night rhythm.** Day is short, gentle, talkative; night is the bullet heaven.
4. **One signature mechanic** — the **grave-lantern cone** is your only weapon at start; everything else is the necro-army you grow.
5. **5-minute runs.** A night is 5 minutes. Repeated, varied, replayable forever.

## 2. Core game loop

```
Day (3 min): tend graveyard, plant, talk to mourner, choose tonight's upgrade
↓
Night (5 min): hold grave-lantern, sweep souls, reap the violent, guide the gentle
↓
Dawn cinematic: army updates, garden state updates, journal entry
↓
Next day (next graveyard or same one harder)
```

## 3. Player verbs

| Verb | Input | Notes |
|---|---|---|
| Move | WASD / left stick | Always-on |
| Aim lantern cone | Mouse / right stick | The cone is your only direct weapon |
| Hold to charge | LMB hold | Charges to a wide sweep |
| Guide (pacifist) | E near a Gentle Soul | Soul follows player to its grave — score bonus |
| Reap (necromancer) | Soul auto-reaps when killed by lantern | Adds to your necro-army |
| Plant moonflower | Day only, F | One per garden patch |
| Talk to mourner | E near mourner | Branching `DialogueNodeSO` |
| Open journal | J | Pause; review army composition, garden state, deaths catalogued |
| Pause | Esc | Always-safe pause |

**Auto-mechanics:** Lantern fires automatically in a cone in your facing direction. Your necro-army auto-attacks. Player skill = positioning + upgrade choices.

## 4. Necro-army (bounded, post-Cycle 2)

Diego's Cycle 2 ask: **strict cap to prevent late-game performance cliff.**

- **Max army size: 24 units total.**
- 6 archetypes: **Skeleton, Wraith, Banshee, Lich, Revenant, Gravewing**
- Each archetype has 3 evolution tiers (24 final units across mix).
- When at cap, reaping a new soul replaces your lowest-tier same-archetype unit — *strategic over additive*.

## 5. Upgrade trees (per-run + meta)

### Per-run (chosen between nights)
- 5 lantern upgrades (longer cone, brighter, dual-cone, holy-radius, soul-magnet)
- 5 army upgrades (faster, hardier, ranged, summoner, swarm)
- 5 garden upgrades (more flowers, healing flora, defensive thorn-vines, soul-attractor)

### Meta-progression (between graveyards)
- 6 **Heirlooms** (passive bonuses unlocked by completing each graveyard)
- **Wren's grandmother's locket** — starts with 1 charge of revive; upgrades to 3 over the game
- Cosmetic: 12 lantern skins, 8 outfits, 6 garden palettes (DLC-friendly)

## 6. Mission structure — 6 Graveyards

| # | Graveyard | Theme | Boss |
|---|---|---|---|
| **1** | *The Old Yard* | Tutorial; Wren's home | The Restless Caretaker (M1 boss) |
| 2 | *The Mourning Path* | Roadside cemetery; introduces ranged souls | The Veiled Walker |
| 3 | *Crypt of Forgotten Names* | Stone catacombs; tight corridors | The Forgotten King |
| 4 | *Lavender Mausoleum* | Cozy-peak; gentlest visuals; hardest cipher boss | The Mourning Bride |
| 5 | *Hollow Mire* | Bog with rising water; movement-puzzle layer | The Drowned Choir |
| 6 | *The Pale Reaper's Field* | Finale | The Pale Reaper |

Each graveyard = ~5 nights to complete (25 minutes). Bosses on night 5. Full game completion ~15h; full mastery (all heirlooms, all cosmetics) ~20–25h.

## 7. Mission 1 — *The Old Yard*

**Goal:** Onboard the player into day-talk, planting, night-sweep, soul-reap. **Duration:** ~12 minutes total (3 min day + 5 min night + 3 min boss + 1 min dawn).

**Cinematic moment (trailer-shaped):** Wren raises the grave-lantern for the first time. The flame catches. A single ghost-light rises from a grave and tilts toward her. *That* shot.

**Flow:**
1. Day intro: grandmother's letter on the cottage table; Wren walks out to find the gate creaking.
2. Garden tutorial: plant 1 moonflower; talk to Mrs. Holloway (mourner) at the gate.
3. First night begins. Grave-lantern lights automatically.
4. **Gentle Soul** appears (small, slow, glowing soft white). Player can guide (E) or sweep with lantern (will dissipate).
5. **Restless Soul** appears (red-eyed, faster). Player must lantern-sweep — reap.
6. After ~30 reaps, a wave concludes; *The Restless Caretaker* mini-boss appears.
7. Defeat. Dawn cinematic. Wren's first necro-army unit (a skeleton with a watering can) follows her home.

**Objectives (in MissionDataSO):**
- `m1_read_letter` (1)
- `m1_plant_moonflower` (1)
- `m1_talk_mrs_holloway` (1)
- `m1_guide_first_gentle` (1, optional)
- `m1_reap_first_restless` (1)
- `m1_complete_wave_1` (30 reaps)
- `m1_defeat_caretaker` (1)

## 8. The "gentle souls" pacifist track (Cycle 2 required change — Yusuf)

Not every soul is an enemy. Roughly 20% of each night's spawns are **Gentle Souls** — they wander, glow soft white, are not aggressive. The player has two options:
- **Guide them home** (interact with the soul, then with their grave) — score bonus, +1 reputation with the local mourners, no army unit.
- **Sweep them with lantern** (treat them like enemies) — they dissipate, no army unit, small reputation hit.

This ensures the cozy framing is mechanically real, not cosmetic. Players who lean pacifist unlock the "Gentle Path" alternate ending where Wren keeps her grandmother's promise.

## 9. UI

| Screen | Asset |
|---|---|
| Main menu | Heat UI (re-skinned to soft lavender) |
| HUD | Bamao with custom moonflower icon set |
| Upgrade selection | Custom panel with 3-of-15 random pick |
| Pause / journal | Bamao + custom |
| Day shop / mourner dialogue | Pixel Crushers Dialogue UI |

## 10. Audio (Hiroshi)

Commission **4 tracks**: title (piano + cello), day (acoustic + flute), night (choir + soft synth), finale (full orchestral). Diegetic SFX: lantern hum, bone clatter, soul-reap chime, moonflower bloom. Game UI & Puzzle SFX Pack supplies UI.

## 11. Accessibility (Cycle 2 required change — Priya)

- **Camera-shake toggle** + **flash toggle** (photosensitivity — critical for bullet-heaven genre).
- Auto-attack pace setting (no manual click needed; player can focus on positioning).
- Subtitle for all dialogue + boss intros.
- Dyslexia font option.
- Colourblind palette for soul types (Gentle Souls always have an additional shape cue).
- One-handed control layout.
- Difficulty: Story / Standard / Reaper.

## 12. Visual identity (Elena)

Pixel art at 64x64 character scale (consistent with VS / Brotato). Palette locked: **lavender, moss, sage, bone-white, candle-gold, soft oxblood**. References: Spiritfarer (warmth), Coffin of Andy and Leyley (tone, but inverted to cozy), Eastward (palette mood). One pixel artist contracted for full project = style coherence.

## 13. Cut-list (if scope slips)

1. Graveyard 5 (Hollow Mire) collapses to a sub-area of Graveyard 4.
2. 6 of 24 cosmetic outfits.
3. Switch port (defer to post-launch).
4. Voice acting (lean fully on text + audio cues).

**Never cut:** Mrs. Holloway, the first lantern-strike cinematic, the Gentle Path ending.

✅ **Approved by Creative Director + 14-expert Cycle 2 (with 3 required changes applied).**
