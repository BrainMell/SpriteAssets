# SpriteAssets

RPG sprite assets for whatsapp-bot.

**Branch: `audit/organize-assets`** — this branch is mid-cleanup. The repo is split into exactly two top-level folders so it's always clear what's been processed and what hasn't:

## `organized-by-agent/` — 655 files, cropped/identified/renamed

Everything in here has been individually cropped into per-frame files with descriptive names and sorted into folders. See `organized-by-agent/AGENT_HANDOFF.md` for full history and naming conventions.

| Folder | Contents | Frames |
|---|---|---|
| `creatures/bat/` | Bat sheet, alpha-cropped | 35 |
| `creatures/kobold/` | Kobold sheet, alpha-cropped | 54 |
| `creatures/sahuagin/` | Sahuagin sheet, alpha-cropped | 45 |
| `creatures/skeleton_warrior/` | Skeleton warrior sheet, alpha-cropped | 57 |
| `creatures/troll/` | Troll sheet, alpha-cropped | 36 |
| `creatures/wolf/` | Wolf sheet, alpha-cropped | 54 |
| `props/training-dummy/` | Training dummy sheet, alpha-cropped | 54 |
| `props/turnip-creature/` | Turnip creature sheet, alpha-cropped | 54 |
| `props/tree-of-glory/` | `tree_of_glory_idle-Sheet.png`, uniform-grid cropped | 43 |
| `sprites/*/` (16 subfolders) | Base/attack/idle sheets, cropped per-creature. **Naming is best-effort color+silhouette** (not confirmed species) — flagged for human spot-check | 160 |
| `sorted-screenshots/*/` (4 subfolders: `animated-effects`, `icons-small`, `portraits-large`, `misc-sprites`) | 62 loose clipboard screenshots, sorted by type/size. **Category-level only**, not individually renamed | 62 |

Naming convention for cropped frames: `{creature}_{color/material}_{trait or weapon}_{action-pose-description}_frameNN.png`

## `raw-asset-packs/` — 1815 files, untouched

Every original asset pack and loose file that has **not** been processed: `Bonus Pack 2025`, `Dark VFX 1/2`, `Holy VFX 01/02`, `Icons_Essential`, `Shikashi's Fantasy Icons Pack` (+ variants), `Zombies`, `Retromon Free Pack`, `boss_0_N.png` through `boss_13_S.png`, `Rat_0004_dark.png`, `Werewolf_0004_brown.png`, `Tree_of_Glory-Sheet.png` (note: different file from the one already processed — this one still has capital letters and no `_idle`), and everything else. Nothing in here has been renamed, cropped, or identified. If it's not in `organized-by-agent/`, it's raw.

## Status

- ✅ Batch 1 (6 creature sheets + 2 prop sheets): done
- ✅ Tree of Glory idle sheet: done
- ✅ `sprites/` folder (16 creatures): done, needs spot-check on naming
- ✅ 62 loose screenshots: sorted by category, not individually named
- ⬜ Everything in `raw-asset-packs/`: not started
