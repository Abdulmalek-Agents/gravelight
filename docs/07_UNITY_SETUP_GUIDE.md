# 🛠 Unity Setup Guide — Gravelight

## 1. Prerequisites

- Unity Hub installed
- Unity **6 LTS (6000.4.4f1)** installed via Unity Hub
- Git installed
- 4 GB free disk

## 2. Clone & open

```bash
git clone https://github.com/Abdulmalek-Agents/gravelight.git
cd gravelight
```

In Unity Hub: **Add → Open existing project → select `gravelight/`**.

## 3. Set render pipeline (2D-URP)

Project Settings → Graphics → Scriptable Render Pipeline → assign `URP-2D` asset.

## 4. Verify Burst + Jobs packages

Window → Package Manager → install / confirm:
- Burst (latest)
- Collections
- Mathematics
- 2D Animation
- New Input System

These are required for the 500-entity perf path.

## 5. Import Asset Store packs

Log into Unity Asset Store with the Inventix account. From Package Manager → My Assets, import:

| Pack | Folder destination |
|---|---|
| Casual RPG VFX | `Assets/_ThirdParty/CasualRPGVFX` |
| Lumen Stylized Light FX 2 | `Assets/_ThirdParty/LumenFX2` |
| Bamao Pack Fantasy GUI | `Assets/_ThirdParty/Bamao` |
| Heat Complete Modern UI | `Assets/_ThirdParty/Heat` |
| Game UI & Puzzle SFX Pack | `Assets/_ThirdParty/GameUISFX` |
| Pixel Crushers Dialogue System | `Assets/_ThirdParty/PixelCrushers` |
| Cutscene Engine | `Assets/_ThirdParty/CutsceneEngine` |
| Screenspace VFX | `Assets/_ThirdParty/ScreenspaceVFX` |

## 6. Must-buy: Pixel Necromancy pack

Buy one of:
- Asset Store "Pixel Necromancy Pack" (~$40), OR
- Commission single pixel artist for full project (preferred for coherence)

Place in `Assets/_ThirdParty/NecroPack/`.

## 7. Performance bench (mandatory before Phase 2)

Open `Scenes/PerfBench.unity`. Press Play. The scene spawns 500 dummy souls + 24 dummy army units. **Frame time must stay under 16ms on Steam Deck or comparable integrated GPU.**

If failing:
1. Confirm Burst is enabled (Project Settings → Burst).
2. Confirm SRP Batcher is enabled.
3. Confirm all soul instances share one material.
4. If still failing: scope to 300 souls + 16 army (documented fallback in Production Plan §1).

## 8. Wire prefabs

1. Open `Scenes/Bootstrap.unity`. Press Play — title card.
2. Open `Scenes/Graveyard_01_OldYard.unity`. Drag `Prefabs/Player/Wren.prefab` into the scene.
3. Drag `Prefabs/Souls/SoulSpawner.prefab`. Set `SoulDataSO` references.
4. Drag `Prefabs/Bosses/RestlessCaretaker.prefab`.
5. Press Play. First night should start within 3 seconds of dialogue end.

## 9. Build target

- File → Build Settings → Windows + Mac + Linux
- IL2CPP scripting backend for release
- Switch (post-launch): Unity Switch SDK setup separately

## 10. No proxy server, no API key, no internet required

The shipping game is fully offline. There is no runtime LLM call.

## 11. Troubleshooting

| Symptom | Fix |
|---|---|
| Frame rate <60fps | Run PerfBench scene; verify Burst + SRP Batcher |
| Pink materials | Project not on URP-2D — re-assign in Graphics settings |
| Souls clipping through each other | Spatial-grid resolution too coarse — reduce cell size to 16 |
| Photosensitivity flash too intense | Confirm flash-toggle in settings is wired to ScreenspaceVFX intensity |
