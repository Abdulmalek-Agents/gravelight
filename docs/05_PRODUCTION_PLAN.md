# 📅 Production Plan — Gravelight

> 9-month ship plan. Phases are ordered; specific durations are realistic but flex with team availability.

## Team

- 1× Lead designer/programmer (full-time)
- 1× Pixel artist (part-time, 4 months commissioned)
- 1× Composer (commissioned, 6 weeks)
- Optional: 1× QA tester (last 4 weeks)

Total payroll + commissions estimate: **$15–30k**.

## Phase plan (9 months)

### Phase 1 — Engine + Perf Foundation
*Output: 500 entities @ 60fps perf test passing on Steam Deck*

- Set up Unity 6 LTS 2D-URP project
- Implement ServiceLocator, SaveService, EventBus
- Implement Jobs + Burst spatial-grid soul movement
- Implement LanternCone + collision queries
- Performance bench: 500 dummy souls + 24 dummy army on Steam Deck → must hit 60fps
- Internal milestone: tech bar cleared. **If failed, scope cut: max army size 16, max souls 300.**

### Phase 2 — Vertical slice (Old Yard M1)
*Output: Steam Next Fest-ready demo (one full night, ~12 min)*

- Commission pixel artist: Wren + 8 souls + 1 boss (Restless Caretaker)
- Commission composer: 2 tracks (title + Old Yard night)
- Author Old Yard graveyard + Mrs. Holloway mourner
- Implement Day phase (planting, dialogue, upgrade-pick)
- Implement Night phase (waves, boss, dawn cinematic)
- Polish accessibility (camera-shake toggle, flash toggle, font, palette)
- Internal milestone: Mission 1 full playthrough

### Phase 3 — Graveyards 2–3 + Steam page
*Output: Steam page live, ~30 min content beyond demo*

- Commission pixel artist: 12 more souls, 2 bosses
- Compose: 1 more track (variety night)
- Author Graveyards 2 & 3
- Implement 5 lantern + 5 army + 5 garden upgrade tree
- Publish Steam page; submit to Steam Next Fest

### Phase 4 — Steam Next Fest + wishlist push
*Output: Public demo, 8,000 wishlists target*

- Demo polish
- Creator outreach (Olexa, Retromation, Splattercatgaming, Wanderbots)
- TikTok shorts (1/week)
- Reddit AMAs: r/VampireSurvivors + r/roguelites + r/CozyGamers
- Internal milestone: 8,000 wishlists

### Phase 5 — Graveyards 4–6 + Pale Reaper
*Output: complete game build*

- Commission pixel artist: 10 more souls, 3 final bosses
- Compose: 1 more track (finale)
- Author Graveyards 4, 5, 6
- Implement Heirloom meta-progression
- Implement "Gentle Path" alternate ending
- Implement all 24 cosmetic outfits / lantern skins

### Phase 6 — Polish + accessibility certification + cert prep
*Output: cert-ready build*

- Full accessibility pass (Priya's spec)
- Steam achievements (~25)
- Steam Cloud save
- Steam Deck verified submission
- Closed beta with ~50 VS-community testers
- Photosensitivity certification check (EPS-3 test pass)

### Phase 7 — Launch
*Output: Day 1 release*

- Steam Day 1 1.0 launch at $9.99
- Switch port build in parallel; aim for +90 day Switch release
- Live community moderation (Amara)
- Patch hotfixes

### Phase 8 — Post-launch (3 months tail)
*Output: 2 free updates + Switch release + paid DLC*

- Free Update 1: "The Beekeeper" — new mourner, 5 new souls
- Free Update 2: New Game+ mode
- Switch port release
- Paid DLC 1: "The Lighthouse Yard" ($4.99, new graveyard + boss + heirloom)

## Risk register

| Risk | Mitigation |
|---|---|
| Performance gate failed at Phase 1 | Scope-cut to 300 enemies + 16 army (still genre-competitive) |
| Pixel artist scope creep | Lock contract: 40 enemies + 6 bosses + Wren + Mrs. Holloway + 5 other mourners |
| Composer delay | Royalty-free fallback OST queued for placeholders |
| Vampire Survivors 2 announcement | Monitor monthly; can shift launch ±60 days |
| Photosensitivity certification fail | Phase 6 explicit gate; cannot launch without EPS-3 pass |

## Budget breakdown

| Item | Cost |
|---|---|
| Lead designer/programmer (9 mo, part-time equiv.) | $14,000 |
| Pixel artist | $300–1,500 |
| Composer | $200 |
| Bespoke SFX | $100 |
| Asset Store must-buys | $40 |
| Marketing (Next Fest, X ads) | $1,000 |
| Switch port (if internal dev license) | $0 |
| Contingency 20% | $3,500 |
| **Total** | **$19,140–20,340** |

Fits the $15–30k envelope comfortably.
