# Reference Categories
<!-- Lightweight index for scaling beyond the core set. -->
<!-- Read this when _core.md doesn't have what you need. -->
<!-- Then load only the specific sub-folder or image required. -->

## vv-style/shapes/

| Folder | Contents | Count | Load when... |
|--------|----------|-------|--------------|
| circles/ | hollow ring, solid dot, merge sequence, bright-vs-dim pair | 10 | scene uses a standalone circle or circle transition |
| rectangles/ | portrait rect, landscape rect, progress bars (outline + fill states) | 9 | scene uses a page/document/frame/bar shape |
| triangles/ | up-solid, down-solid, up-outline, right-pointing | 2 | scene uses hierarchy/leverage/direction |
| lines/ | horizontal, vertical, vertical-bars-comparison (earn/spend), ascending staircase bars | 12 | scene uses a baseline, divider, axis, or bar comparison |
| compound/ | book-open, circle-between-options, growth-curve-comparison, fan-arrows, input-into-process, content-density-scale, arrow-x-emphasis-swap, rect-frame-signal-noise, curve-spike-vs-flat, circle-solid-vs-dot-grid | 38 | scene uses a multi-element or symbolic shape |

## vv-style/movements/

| Folder | Contents | Count | Load when... |
|--------|----------|-------|--------------|
| drops/ | ball drop, shape fall, cascade | 0 | element arrives from above |
| rises/ | ball rise, float up | 0 | element exits upward |
| turns/ | page turn, rotation, flip | 0 | element rotates or pages change |
| morphs/ | rect→oval, expand, collapse | 0 | element changes shape |

## vv-style/layouts/

| File | Contents | Load when... |
|------|----------|--------------|
| complexity-to-simplicity.png | V.1 chaotic grid vs V.674 clean rect — the VV design philosophy itself | studying the meta-principle of simplification |
| rect-jpg-vs-nft.png | two landscape rects with labels; only color image in library (blue badge) | scene needs a labeled card comparison or provenance concept |
| text-label-pair.png | two small-caps labels widely spaced — reference for VV label typography | studying label/axis label conventions |
| (17 additional layout images) | full-bleed compositions, text-over-shape layouts, multi-panel arrangements | studying full-frame layout and text placement | **Count: 17 total**

## vv-style/effects/
*(4 files — glow, shadow, and texture examples)* **Count: 4**

## vv-style/movements/
*(8 files — drop, rise, turn, morph sequences)* **Count: 8**

---

## File naming convention
`[descriptor]-[variant].png`
Examples: `circle-merge-sequence.png`, `bars-ascending-staircase.png`, `curve-spike-vs-flat.png`

## Adding new shapes
1. Drop the PNG into the correct subfolder with the descriptive name from catalog.md
2. Update the count in the table above
3. If archetypal (reused often) → add SVG snippet to `_core.md`
4. If one-off → catalog.md entry is enough

<!-- Batch 1: 16 images analyzed · 7 new shapes in _core.md · folders created -->
<!-- PNGs pending manual placement — see catalog.md for filename → folder mapping -->
