# SpriteAssets

Reorganized asset pool for MicroLoan/other Go+Flutter side projects using pixel art.
Structure below reflects the `organize-assets` branch cleanup (dedupe + categorize).
Old README content preserved in `README.old.md.bak`.

## What changed

- Removed `__MACOSX` junk folders (Mac resource-fork noise, zero content).
- Deduped exact-copy folders: `Zombies (1)`, `German shepard bundle (1)`,
  `Shikashi's Fantasy Icons Pack v2 (1)`, and `Sperites/` (byte-identical dupes
  of files that also lived loose in root). ~25MB removed, no asset loss.
- `graphics/` left untouched — this looks like an already-organized live game
  asset tree (attacks/backgrounds/characters/fonts/icons/monsters/objects/
  tilesets/ui), so it wasn't restructured beyond restoring what a stray move
  briefly pulled out.

## Folder guide

- **`creatures/`** — anything monster/creature related
  - `unnamed_creature_set/` — the old anonymous `sprite1.png`...`sprite16.png`
    (+ `_attack`/`_idle` variants). I looked at each and renamed by what's
    actually drawn, e.g. `toad_green_walk.png`, `drake_red_attack.png`,
    `spider_dark_idle.png`. Full list: toad_green, rat_grey, wolf_brown,
    fox_orange, jelly_purple, bat_dark, slime_teal, chick_yellow, sprout_green,
    spider_dark, golem_brown, ghost_grey, drake_red, fish_blue, beetle_navy,
    serpent_green. (Best-effort visual ID off small pixel art — flag me if any
    look wrong and I'll fix the name.)
  - `raw_sheets_to_crop/` — full, uncut sprite sheets (sahuagin, skeleton,
    slime, troll, wolf, kobold, bat, rat, werewolf, crab, gnoll, goblin,
    turnip, training dummy, tree of glory, blue doom, fire fear, espantalho,
    dragon). Names are already descriptive; these still need per-frame
    cropping before use — that's the next pipeline step.
  - `retromon_pack/` — the free fakemon-style variety pack (53+ creatures),
    left in its original internal structure since it's already clean.

- **`vfx_and_spells/`** — Dark VFX 1/2, Holy VFX 01/02, Magic Pack, the
  `128/64/32` icon-size folders, attack effects.

- **`ui_and_icons/`** — FantasyUIfree, Icons_Demo/Essential, both Shikashi
  icon packs, animated key pack, UI/UI_Elements_Demo.

- **`character_packs/`** — German shepherd bundle, Zombies, Bonus Pack 2025,
  Humble Gift, character overworld, menu sprites, and `impact_gifs/` (the
  loose scratch/spark hit-effect GIFs from root).

- **`tilesets_and_backgrounds/`** — tileset, backgrounds, SD.

- **`bosses/`** — the `boss_N_N.png` / `boss_N_S.png` directional sprite set.

- **`effects_misc/`** — loose `die.png`, `idle.png`, `walk.png`,
  `magical attack.png` (unclear which pack these belong to — didn't want to
  guess-merge them into a named pack).

- **`_unsorted_review/screenshots_and_clipboard/`** — 58 auto-named clipboard
  dumps (`image - 2025-08-16T...png`, `image (N).png`, a few gifs). Didn't
  burn the budget eyeballing all 58 — say the word and I'll go through them
  and sort/label properly, or if you know what date range matters most I can
  start there.

## `creatures/cropped_frames/` — frame-by-frame cuts, ultra-detailed names

Every sheet in `raw_sheets_to_crop/` has now been cropped into individual
frames using alpha-channel bounding-box detection (for packed/variable-width
sheets) or exact uniform-grid math (for sheets that divide evenly by their
own height, e.g. `tree_of_glory` at 512×512×43).

**1,124 frames total**, 17MB, one folder per creature. Filename pattern:

```
{creature}_{color/variant if known}_{action}_frame{NN}of{total}.png
```

e.g. `sahuagin_idle_frame00of09.png`, `kobold_red_attack_frame04of09.png`,
`wolf_brown_death_frame08of09.png`.

**Action labels (idle/walk/run/attack/hurt/death) are inferred from row
order** — 14 of these sheets share an identical 6-row × 9-frame layout,
which is the standard action ordering for this asset-pack style. I did **not**
visually confirm every single row's action per creature (that'd be 84+ manual
checks) — if GLM or you spot a mislabeled row (e.g. row 3 is actually "cast"
not "attack" for some creature), tell me which one and I'll relabel just that
folder rather than guessing wrong across all of them.

Sheets processed: sahuagin, skeleton, troll, wolf, kobold, bat, rat,
werewolf, training-dummy, turnip, crab, gnoll, goblin, slime (all 6×9 =
54-57 frames each) + tree-of-glory (43-frame uniform idle strip) +
blue-doom, espantalho, espantalho-antigo, fire-fear (uniform VFX/summon
strips) + dragon-pixel (small 17-frame irregular sheet).

Original uncut sheets are still in `raw_sheets_to_crop/` in case a re-crop
is ever needed.

## Still open

- `_unsorted_review/` (58 clipboard screenshots) needs a manual pass.
- Row/action labels above are convention-based, not frame-by-frame verified —
  flag anything that looks wrong.
