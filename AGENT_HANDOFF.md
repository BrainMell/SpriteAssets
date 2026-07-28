# Sprite Asset Reorg — Handoff Notes

Repo: `BrainMell/SpriteAssets`
Branch: `audit/organize-assets` (already pushed, safe to build on)

## Done (batch 1 — pushed)
- Deduped `German shepard bundle (1)/` — was byte-identical to `German shepard bundle/`, removed.
- Cropped and ultra-detail-renamed 8 raw sprite sheets using alpha-channel boundary detection
  (no manual grid guessing — script finds actual transparent gaps between frames):
  - `creatures/sahuagin/` (45 frames)
  - `creatures/skeleton_warrior/` (57 frames)
  - `creatures/troll/` (36 frames)
  - `creatures/wolf/` (54 frames)
  - `creatures/kobold/` (54 frames)
  - `creatures/bat/` (35 frames)
  - `props/training-dummy/` (54 frames)
  - `props/turnip-creature/` (54 frames)

**Naming convention** (keep this consistent):
`{creature}_{color/material}_{trait or weapon}_{action-pose-description}_frame{NN}.png`
e.g. `skeleton-warrior_bone-white_red-cape_hurt-recoil-staggering-sword-and-shield_frame03.png`

## Not done yet — needs a session with working vision
1. **`sprites/` folder** — 16 unidentified creatures (`sprite1.png`...`sprite16.png`), each with
   `_attack` and `_idle` variants too (48 files total). These have no descriptive filenames at all,
   so they need to actually be looked at and identified from scratch. Base files are 192x96 —
   likely 2 frames side by side, check before cropping.
2. **41 loose clipboard screenshots** in repo root, named like `image - 2025-08-16T194831.536.png`.
   Need to be opened, identified, and sorted into the right folder (creature sheet? UI element? reference/junk?).
3. **`tree_of_glory_idle-Sheet.png`** — confirmed uniform grid, 512x512 cells, 43 frames, single row,
   idle loop. Just needs cropping + naming, no identification needed, low priority since it's already understood.

## Reusable tooling (already in the sandbox pattern, rebuild if needed)
- `crop_sheet.py` — alpha-channel frame detector, finds sprite boundaries via transparency gaps,
  handles variable-width frames within a row (not just uniform grids).
- `batch_process.py` — groups detected frames into animation rows by y-position (rolling-average
  tolerance, not fixed anchor — fixed anchor drifts and mis-splits rows on sheets with variable
  frame heights), assigns action labels per row, crops+saves with the naming convention above.
- Tune `y_tol` per sheet if row-grouping looks off (tried 50–140 across different sheets depending
  on frame size/spacing — smaller frames need smaller tolerance).

## What went wrong before this session
Prior attempts (Antigravity/Gemini subagents, then a separate Qwen session) tried external vision
APIs and invalid OAuth tokens, hit rate limits, and at one point fabricated descriptions without
actually looking at images (e.g. `boss_3` was never truly identified). This session did real
alpha-based cropping + real visual identification for batch 1, then vision access broke mid-session
(stopped returning results entirely, confirmed via re-testing on already-successfully-viewed files).
No guessing was done to compensate — batch 1 is fully real, everything above is honestly marked
as not-yet-done rather than faked.

## GitHub PAT note
The PAT used to push (`ghp_rUp...`) has been exposed in multiple chat sessions/logs at this point.
Revoke and regenerate before further work if you haven't already.
