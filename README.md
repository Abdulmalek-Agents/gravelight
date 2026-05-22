# 🕯️ Gravelight — The Necromancer's Garden

> *"The dead don't fear the dark. They fear being forgotten. Give them light."*

A **cozy bullet-heaven survivors-like** where you play a kind young necromancer tending an abandoned Victorian graveyard. By day, you garden, mend headstones, and listen to mourners. By night, the restless dead rise — and you must sweep them with your **grave-lantern**, guiding the gentle ones to peace and reaping the violent ones for your growing necro-army. Survive 20 nights to face the Pale Reaper. Lavender-and-moss palette, never grimdark.

**Pitch in one line:** *Vampire Survivors × Stardew Valley's warmth × Spiritfarer's tenderness.*

| | |
|---|---|
| **Genre** | Cozy Bullet Heaven / Survivors-like Roguelite |
| **Platforms** | PC (Steam) primary; Switch + iPad + Android stretch |
| **Engine** | Unity **6 LTS (6000.4.4f1)** |
| **Render** | 2D Universal Render Pipeline (URP-2D) |
| **Target frame-rate** | 60 fps on integrated GPU; 500+ enemies on screen |
| **Mission 1 scope** | *The Old Yard* — first night, tutorial run, first soul reaped |
| **Designed for** | 6 graveyards + bestiary roguelite progression (~15–25h to complete) |
| **Team size** | 1–2 (solo-dev feasible) |
| **Budget** | ~$15–30k |
| **Target ship** | within 9 months from greenlight |
| **Runtime AI features** | **None** — fully offline. Mourner dialogue is hand-authored `DialogueNodeSO` trees. |
| **AI in development** | Claude Code & Claude Agents are used in the studio workflow. See [docs/04_TECHNICAL_ARCHITECTURE.md](docs/04_TECHNICAL_ARCHITECTURE.md). |

## Why this game

Vampire Survivors lifetime revenue is >$100M from a ~$5 game. Brotato sold 4M+. Halls of Torment, 20 Minutes Till Dawn, Death Must Die — the genre keeps minting indie hits. **But every successful entry trades on grimdark, blood, or comedic violence.** Gravelight occupies an empty niche: *cozy necromancy*. Soft palette, gentle music, kind protagonist, comforting framing of death-as-rest. Same gameplay engine the audience loves, paired with the cozy aesthetic that's the fastest-growing wishlist segment on Steam. That double-magnet positioning is the entire commercial bet.

Details in [`docs/01_IDEATION_AND_TRENDS.md`](docs/01_IDEATION_AND_TRENDS.md).

## What's in this repo

```
gravelight/
├── README.md                              ← you are here
├── LICENSE                                ← MIT (original code/docs only)
├── CHANGELOG.md
├── .gitignore                             ← Unity-standard
└── docs/
    ├── 00_PORTFOLIO_REVIEW_BOARD.md       ← 14-expert vote + verdict
    ├── 01_IDEATION_AND_TRENDS.md          ← market evidence
    ├── 02_GAME_DESIGN_DOCUMENT.md         ← full GDD
    ├── 03_ASSET_PLAN.md                   ← Unity Asset Store list (~$60 must-buy)
    ├── 04_TECHNICAL_ARCHITECTURE.md       ← Unity 2D-URP, ECS-lite for 500+ enemies
    ├── 05_PRODUCTION_PLAN.md              ← 9-month phase plan
    ├── 06_CRITIC_REVIEW_CYCLES.md         ← 3-cycle critic review (14 experts)
    ├── 07_UNITY_SETUP_GUIDE.md            ← click-by-click setup
    └── 08_MARKETING_PLAN.md               ← wishlist + Steam Next Fest plan
```

## Quick start

1. Read [`docs/07_UNITY_SETUP_GUIDE.md`](docs/07_UNITY_SETUP_GUIDE.md).
2. New Unity **6 LTS (6000.4.4f1)** 2D-URP project.
3. Import: 2D Animation Package, Bamao Pack Fantasy GUI, Heat UI, Game UI & Puzzle SFX Pack, Casual RPG VFX, Lumen Stylized Light FX 2 — from inventory. Plus must-buy: 2D Cozy Necromancy character/enemy pack (~$40).
4. Open `Scenes/Bootstrap.unity` → Play.

## Status

| Stage | Status |
|---|---|
| 14-expert Cycle 1 vote (concept) | ✅ Approved (avg **8.21/10**) |
| 14-expert Cycle 2 (GDD) | ✅ Approved with 3 required changes (all applied) |
| 14-expert Cycle 3 (architecture + asset + marketing) | ✅ Final Approved (14/14 clean) |
| Mission 1 *The Old Yard* implementation | ⏳ Pending Unity import |
| Graveyards 2–6 outlined | ✅ Data-driven |
| Steam page | ⬜ Schedule for Month 3 |

> Maintained by Abdulmalek-Agents (Inventix Games). PRs welcome.
