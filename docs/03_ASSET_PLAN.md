# 🎨 Asset Plan — Gravelight

> Net coverage from Inventix existing inventory: **~80%**. Must-buy gap is small.

## 1. Existing inventory used

| Asset | Used for | Critical |
|---|---|---|
| **Casual RPG VFX** ($25) | Soul dissipation, lantern cone particle, boss VFX | 🔴 Yes |
| **Lumen Stylized Light FX 2** ($35) | Lantern light, ghost-light glow, moonflower bloom | 🔴 Yes |
| **Bamao Pack Fantasy GUI** ($25) | In-game HUD, upgrade panels, journal | 🔴 Yes |
| **Heat Complete Modern UI** ($69.99) | Main menu, settings (lavender re-skin) | 🔴 Yes |
| **Game UI & Puzzle SFX Pack** ($99) | Menu clicks, upgrade chime, level-up jingle | 🔴 Yes |
| **Pixel Crushers Dialogue System** ($75) | Day-time mourner conversations | 🔴 Yes |
| **Cutscene Engine** ($35) | First-lantern cinematic, boss intros, dawn fades, finale | 🔴 Yes |
| **2D Animation Package** (Unity, free) | Skeleton + soul + Wren animations | 🔴 Yes |
| **Screenspace VFX** ($30) | Low-HP vignette, photosensitivity-aware screen flash (gated by toggle) | 🟡 Helpful |

**Inventory value applied: ~$390.** All packs already owned.

## 2. Gap analysis — must-buy

| Gap | Suggested | Cost |
|---|---|---|
| Player + 30 enemies + 6 bosses pixel art | Asset Store "Pixel Necromancy Pack" OR commission single pixel artist | $40–$300 |
| OST (4 tracks) | Commission composer | $200 |
| Soul / lantern / bone SFX (~25 bespoke) | Commission OR creative-commons mix | $0–100 |
| Switch port build (post-launch) | Internal | $0 |

**Must-buy total — Mission 1:** **~$40** (just enough enemy sprites to run the first night).
**Full game ship total:** **~$500.**

Within the $15–30k team-budget envelope by a large margin.

## 3. Style coherence rule (Elena's Cycle 3 ask)

**One pixel artist for the whole project.** Bullet-heaven games show 100+ sprites on screen simultaneously — any style inconsistency is screaming-visible. Budget ~$300 for one part-time pixel artist over 4 months. If commissioned, lock palette + sprite-scale + animation-frame-count contractually.

## 4. Folder organisation

```
Assets/_Project/
├── Art/{Player,Souls,Bosses,Garden,UI,VFX}
├── Audio/{Music,SFX,Ambient}
├── Animations/
├── Materials/
├── Prefabs/{Player,Souls,Bosses,Garden,UI,VFX}
├── Scenes/
├── Data/{Graveyards,Souls,Upgrades,Mourners,LineBanks,Cosmetics}
└── Scripts/{Core,Combat,Army,Garden,Dialogue,UI,Save,Performance}
```

## 5. Performance tweaks (Diego's ECS-lite plan)

- Souls and necro-army units use **Unity Jobs + Burst** for movement (target 500+ entities @ 60fps).
- Single material for souls (instanced with color/sprite variant).
- Object pooling for all VFX (lantern cone particles, dissipation, soul-reap chime sprite).
- Lantern cone uses a **single rotating Mesh + custom shader**, not Light2D (Light2D cost too high at this entity count).
- Performance budget gate at Month 3: 500 enemies + 24 army units + Wren on integrated GPU @ 60fps.

## 6. Licence audit ✅

Unity Asset Store EULA covers all listed packs (Inventix licences). Commissioned art = work-for-hire with explicit commercial-use buyout. **Asset binaries are NOT redistributed in this repo.**

## 7. Post-purchase checklist

- [ ] Import all Asset Store packs
- [ ] Lavender-skin Heat UI + Bamao
- [ ] Commission pixel artist (full project)
- [ ] Commission composer (4 tracks)
- [ ] Author 6 GraveyardDataSO + 30 SoulDataSO + 6 BossDataSO
- [ ] Author 6 MournerSO (with `DialogueNodeSO`)
- [ ] Build Wren_Player.prefab (auto-lantern + movement)
- [ ] Build NecroArmyController + 6 archetype prefabs
- [ ] Build SoulSpawner with NavMesh-2D + Jobs movement
- [ ] Build BossFlowController (2-phase Animator pattern)
