# 🛠 Technical Architecture — Gravelight

> Unity **6 LTS (6000.4.4f1)** + URP-2D. Single-player. Offline. No networking. The hardest tech constraint is **500+ active entities on screen at 60fps on integrated GPU.**

## 1. Tech stack

| Layer | Choice | Reason |
|---|---|---|
| Engine | Unity 6 LTS 6000.4.4f1 | Stable, current portfolio standard |
| Render | URP-2D | 2D pipeline; necessary for batching |
| Language | C# 10 + Burst-compiled jobs | Standard + perf path |
| Performance backbone | Jobs + Burst (NOT full DOTS) | Right-sized for our scale |
| Data | ScriptableObjects + JSON save | Designer-friendly |
| Save | Custom JSON + Steam Cloud | Run-state + meta-progress |
| Networking | **None** | Single-player |
| Localisation | Unity Localization Package | EN at launch |
| Input | New Input System | KB+M + controller from Day 1 |

## 2. Core architecture

### Service Locator pattern

```
GameBootstrap
  └─ ServiceLocator
       ├─ GraveyardService  (current graveyard, current night, day state)
       ├─ SaveService       (run state + meta-progress JSON)
       ├─ AudioService      (music layers + SFX + ambience)
       ├─ DialogueService   (Pixel Crushers wrapper, scripted)
       ├─ ArmyService       (necro-army cap, archetype counts, replace logic)
       ├─ UpgradeService    (per-run picks, meta heirlooms)
       ├─ SoulSpawnerService(Jobs-driven; pulls from SoulDataSO)
       └─ RuntimePerfService(frame-time monitor; auto-adjusts particle density)
```

### Data layer (ScriptableObjects)

- `GraveyardDataSO` — environment, soul spawn table, boss, music, garden layout
- `SoulDataSO` — sprite, HP, speed, AI behaviour (Gentle/Restless/Boss), reap reward
- `MournerSO` — portrait, dialogue root, faction, gift-thresholds
- `UpgradeSO` — lantern/army/garden tree node
- `HeirloomSO` — meta-progression passive
- `BossDataSO` — multi-phase boss script
- `DialogueNodeSO` — branching scripted dialogue
- `LineBankSO` — variant lines (boss taunt, mourner quip)

## 3. Performance plan (the hard part)

### Goal: 500 souls + 24 army + 1 player + VFX @ 60fps on integrated GPU

- **Movement**: all souls use a single `IJobParallelFor` updating positions in a flat `NativeArray<Soul>`. No MonoBehaviour Update per entity.
- **Rendering**: instanced SpriteRenderers via SRP Batcher; one material for all souls.
- **Collision**: spatial-hash grid (32x32 cells), not Physics2D. Lantern cone queries the grid each tick.
- **VFX**: object pools; max 80 active dissipation particles; LOD0/LOD1 quality presets.
- **Audio**: pool 32 SFX voices; soul-reap chime culled if more than 8/sec.
- **Frame budget**: 16ms total — 4ms physics-grid + 6ms render + 3ms script + 3ms slack.

Diego's go/no-go: at Month 3, must demo 500 entities @ 60fps on a Steam Deck or fail-fast and re-scope.

## 4. Run-loop architecture

```
NightController (state machine)
  ├─ EnterNight()       → freeze player, fade music, spawn first wave
  ├─ WaveLoop()         → every 30 sec, escalate spawn pressure
  ├─ BossPhase()        → night 5: boss only, no minions
  └─ ExitNight()        → dawn cinematic, persist army + heirloom
```

## 5. Save schema (simplified)

```json
{
  "version": 1,
  "meta": {
    "graveyardsCleared": ["old_yard"],
    "heirloomsUnlocked": ["locket_revive"],
    "cosmeticsOwned": ["lantern_brass"],
    "mournersTrusted": ["holloway"]
  },
  "currentRun": {
    "graveyardId": "old_yard",
    "night": 2,
    "armyComposition": {"skeleton":3,"wraith":1},
    "upgrades": ["lantern_brighter","army_swarm_1"],
    "hp": 80
  }
}
```

## 6. Scenes

- `Bootstrap.unity` — service locator, loads MainMenu
- `MainMenu.unity` — title, continue, new run, settings, credits, cosmetics, journal
- `Graveyard_01_OldYard.unity` through `Graveyard_06_PaleReaper.unity`
- `Cottage_Hub.unity` — between graveyards: garden meta-progress, heirloom display
- `Credits.unity`

## 7. AI in development (NOT runtime)

Claude Code & Claude Agents are used for:
- Drafting mourner dialogue (writer rewrites)
- C# scaffolding for the spatial grid + Jobs (programmer reviews)
- Generating spawn-table CSV variations (designer hand-tunes)
- Test-case generation for the performance harness

**Shipping game contains zero runtime LLM calls.**
