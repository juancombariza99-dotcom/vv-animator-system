# VV Reference Catalog
<!-- Running log of all analyzed images. Updated each batch. -->
<!-- Each entry: filename · folder · what it shows · key patterns · SVG notes -->
<!-- Total analyzed: 16 (Batch 1 of ~6) -->

---

## How to place the PNGs
Drop the original file into the folder listed under each entry, renamed to the filename shown.
The catalog + _core.md are the working reference — PNGs are for visual verification only.

---

## Batch 1

---

### `complexity-to-simplicity.png` → `layouts/`
**What it shows:** Two compositions side by side: left labeled "V.1" — a chaotic fragmented grid, squares scattered and misaligned. Right labeled "V.674" — a single clean portrait rectangle outline. The entire VV design philosophy in one image: radical simplification over time.
**Use when:** Explaining the before/after of design refinement. Meta-reference.
**Key patterns:** Fragmented grid = noise, complexity, early state. Clean rect = signal, clarity, mastery.
**SVG note:** The fragmented grid (left) is ~20 small misaligned squares in an erratic cluster. The rect (right) is the standard portrait rect. Labels in small caps below each.

---

### `content-density-scale.png` → `shapes/compound/`
**What it shows:** Three elements in a horizontal row: (1) a single short horizontal line, (2) three stacked horizontal lines (like a paragraph), (3) a 3×3 grid of squares. Represents complexity scaling: one idea → list → matrix.
**Use when:** Showing information density progression, or the difference between a single point, a list, and a system.
**Key patterns:** Stroke weight is uniform and thin throughout. All three elements centered vertically on the same baseline.
**SVG snippet:**
```svg
<!-- Single line -->
<line x1="150" y1="360" x2="230" y2="360" stroke="white" stroke-width="1.5"/>
<!-- Triple stack (paragraph) -->
<line x1="295" y1="348" x2="375" y2="348" stroke="white" stroke-width="1.5"/>
<line x1="295" y1="360" x2="375" y2="360" stroke="white" stroke-width="1.5"/>
<line x1="295" y1="372" x2="375" y2="372" stroke="white" stroke-width="1.5"/>
<!-- 3x3 grid -->
<!-- 3 cols × 3 rows of small squares, ~18px each, 4px gap -->
```

---

### `circle-merge-sequence.png` → `shapes/circles/`
**What it shows:** Four circles in a horizontal sequence showing two circles merging into one: (1) single hollow ring, (2) hollow ring + solid circle overlapping slightly at right, (3) two circles deeply overlapping (intersection fills dark), (4) single solid circle with thin ring outline.
**Use when:** Showing integration, collaboration, two things becoming one, overlap revealing shared value.
**Animation pattern:** Two circles approach from opposite sides → overlap → intersection fills → one solid circle remains.
**Key patterns:** Stroke is thin (~1.5px). The intersection in state 3 shows the overlapping region as a darker filled lens shape. Final solid circle has the ring stroke still visible around it.
**SVG snippet:**
```svg
<!-- State 1: hollow ring -->
<circle cx="203" cy="360" r="42" fill="none" stroke="white" stroke-width="1.5"/>
<!-- State 2: hollow + approaching solid -->
<circle cx="185" cy="360" r="42" fill="none" stroke="white" stroke-width="1.5"/>
<circle cx="227" cy="360" r="42" fill="white" stroke="none"/>
<!-- State 3: deep overlap (use clipPath for intersection) -->
<!-- State 4: solid circle -->
<circle cx="203" cy="360" r="42" fill="white" stroke="white" stroke-width="1.5"/>
```

---

### `circle-hollow-solo.png` → `shapes/circles/`
**What it shows:** A single hollow ring, centered slightly right and up of the canvas center. Completely isolated — just the ring on black.
**Use when:** Showing the self in a neutral/searching state. The foundational ball shape at rest.
**Key patterns:** Very thin stroke (~1–1.5px). Radius ~60–70px. No glow. The gap at top of the ring (very slight) suggests it's drawn with dasharray in an animation.
**SVG snippet:**
```svg
<circle cx="203" cy="360" r="65" fill="none" stroke="white" stroke-width="1.5"/>
```

---

### `circle-bright-vs-dim.png` → `shapes/circles/`
**What it shows:** Two hollow circles side by side. Left: full-brightness white ring. Right: very low opacity ring (roughly 15–20% white, nearly invisible against black).
**Use when:** Showing visibility vs invisibility, known vs unknown, the seen vs the unseen. Also useful for "before" (dim, unformed) vs "after" (bright, present).
**Animation pattern:** Fade dim ring up to full brightness — the thing becoming real/visible.
**Key patterns:** Same size, same stroke weight. The only difference is opacity. The right circle has a very subtle gray tone.
**SVG snippet:**
```svg
<circle cx="160" cy="360" r="65" fill="none" stroke="white" stroke-width="1.5"/>
<circle cx="310" cy="360" r="65" fill="none" stroke="white" stroke-width="1.5" opacity="0.15"/>
```

---

### `circle-solid-vs-dot-grid.png` → `shapes/compound/`
**What it shows:** Left: a large solid white circle (~130px radius). Right: a 6×6 dot grid, each dot a tiny white circle (~3px radius), arranged in a neat matrix. Shows concentration vs distribution: one dense thing vs many distributed points.
**Use when:** One vs many, singular vs plural, mass vs network, product vs audience.
**Key patterns:** The solid circle is very large — visually dominant. The dot grid is smaller but has 36 points. The contrast in visual weight is the message.
**SVG snippet:**
```svg
<!-- Solid circle (large) -->
<circle cx="170" cy="360" r="110" fill="white"/>
<!-- 6x6 dot grid, 20px spacing -->
<!-- col offset ~310, row offset ~260 -->
<circle cx="310" cy="268" r="3" fill="white"/>
<!-- ... repeat for 36 dots at 20px intervals -->
```

---

### `rect-jpg-vs-nft.png` → `layouts/`
**What it shows:** Two landscape rectangles side by side, both solid white fill with black text centered inside. Left: "JPG". Right: "NFT" with a blue verification checkmark badge in the top-right corner. Labels in bold caps.
**Use when:** Showing how provenance/verification changes what an identical thing is worth. The same object, different context.
**Key patterns:** Only image in the library using color (the blue badge). The rectangles are landscape orientation (~340×200px). Text is centered. The checkmark is small, positioned at the top-right corner of the NFT rectangle.
**Note:** The blue badge is a one-off — VV is otherwise entirely black and white. Use this as a reference for "how a small colored element can carry all the meaning."

---

### `arrow-x-emphasis-swap.png` → `shapes/compound/`
**What it shows:** Two compositions of "arrow → X". Left: dim/gray arrow + bright white X. Right: bright white arrow + dim/gray X. The brightness swaps between the two states — the relationship between process (arrow) and outcome (X), or between cause and effect.
**Use when:** Showing what matters more: the doing (arrow) or the result (X). Before/after. Signal shifting.
**Animation pattern:** Arrow brightens as X dims (or vice versa) to shift emphasis between two elements.
**Key patterns:** Arrow is a horizontal line with arrowhead (~100px long). X is a small cross (~12px). Both elements are same size in both compositions. Dim state is roughly 30–40% white opacity.
**SVG snippet:**
```svg
<!-- Composition 1: dim arrow, bright X -->
<line x1="160" y1="360" x2="250" y2="360" stroke="rgba(255,255,255,0.35)" stroke-width="1.5"/>
<polygon points="250,355 260,360 250,365" fill="rgba(255,255,255,0.35)"/>
<line x1="272" y1="350" x2="284" y2="370" stroke="white" stroke-width="1.5"/>
<line x1="284" y1="350" x2="272" y2="370" stroke="white" stroke-width="1.5"/>
<!-- Composition 2: bright arrow, dim X -->
<line x1="600" y1="360" x2="690" y2="360" stroke="white" stroke-width="1.5"/>
<!-- ... -->
```

---

### `rect-frame-signal-noise.png` → `shapes/compound/`
**What it shows:** A continuous chaotic zigzag line running the full width of the canvas in gray/dim. A white rectangle "frame" overlays the center-left portion — inside the frame the same line continues in bright white. The frame selects/isolates the signal from the noise.
**Use when:** Focus, framing, attention, signal vs noise, what you choose to look at. The rect isn't a container — it's a lens.
**Animation pattern:** Zigzag draws across full width (dim/gray), then rect appears and the portion inside lights up white.
**Key patterns:** The line runs at medium amplitude zigzag (~30px peak-to-peak). The rect is portrait-ish. Inside/outside distinction is purely a color split — the line path is continuous.
**SVG snippet:**
```svg
<!-- Full noisy line (dim) -->
<polyline points="100,320 140,390 180,310 220,380 260,300 300,370 340,295 380,365 420,305"
  fill="none" stroke="rgba(255,255,255,0.3)" stroke-width="1.5"/>
<!-- Rect frame (clips/highlights center portion) -->
<rect x="220" y="270" width="160" height="200" fill="none" stroke="white" stroke-width="1.5"/>
<!-- White portion of line inside rect (redraw the segment) -->
<polyline points="220,380 260,300 300,370 340,295 380,365"
  fill="none" stroke="white" stroke-width="1.5"/>
```

---

### `rect-bars-outline.png` → `shapes/rectangles/`
**What it shows:** Three thin horizontal rectangle outlines (pill/bar shapes) in a row, each roughly the same width (~150px) and very low height (~12px). Outline only — thin white stroke.
**Use when:** Progress bars, loading states, duration bars, any "segment of time or capacity." As outlines = empty/unfilled state.
**Key patterns:** Very thin height (acts more like a thick line than a rect). Uniform width. Evenly spaced horizontally.
**SVG snippet:**
```svg
<rect x="130" y="354" width="150" height="12" fill="none" stroke="white" stroke-width="1.5" rx="2"/>
<rect x="420" y="354" width="150" height="12" fill="none" stroke="white" stroke-width="1.5" rx="2"/>
<rect x="710" y="354" width="150" height="12" fill="none" stroke="white" stroke-width="1.5" rx="2"/>
```

---

### `rect-bars-fill.png` → `shapes/rectangles/`
**What it shows:** Three horizontal bars (same shape as above) but partially or mostly filled solid white from the left, like loading/progress bars. Left bar: ~85% full. Middle: ~65% full. Right: ~50% full. Shows progressive fill states.
**Use when:** Showing fill level, completion percentage, capacity, or the animation of something filling up.
**Animation pattern:** Rect outline → white fill grows left-to-right (scaleX from 0 to 1, transformOrigin left).
**SVG snippet:**
```svg
<!-- Bar + fill layer inside -->
<rect x="130" y="354" width="150" height="12" fill="none" stroke="white" stroke-width="1.5"/>
<rect id="bar-fill" x="131" y="355" width="126" height="10" fill="white"/>
<!-- Animate width of fill rect: 0 → 126 (scaleX 0 → 1) -->
```

---

### `input-into-process.png` → `shapes/compound/`
**What it shows:** An exclamation mark (!) on the left with a horizontal line extending right, feeding into an open-left rectangle (top, right, bottom sides only — open on left). CONFIRMED match for existing _core.md shape.
**Use when:** Trigger entering a system, attention as input, signal → process, cause entering effect.
**SVG snippet:** See _core.md for full snippet. This image confirms the layout.

---

### `text-label-pair.png` → `layouts/`
**What it shows:** Two small caps text labels — "DONE" on the left, "P" on the right — widely spaced on a horizontal axis. Likely "DONE" vs "PENDING" (or "P" is a placeholder). Text-only composition.
**Use when:** Two-state labeling — complete vs incomplete, binary status. Also a reference for VV's label typography style.
**Key patterns:** Small caps, very light weight, widely spaced (letter-spacing ~3px). Labels act as axis labels or state descriptors. Font appears to be a condensed mono or geometric sans.

---

### `bars-earn-spend.png` → `shapes/lines/`
**What it shows:** Two side-by-side pairs of vertical lines, each pair labeled EARN and SPEND below. Left pair: EARN and SPEND are same height (break even). Right pair: EARN taller, SPEND shorter (surplus). CONFIRMED match for existing _core.md vertical-bars-comparison shape.
**Use when:** Financial flows, any two-quantity comparison (input vs output, cost vs revenue).
**SVG snippet:** See _core.md. Labels in small caps below each bar.

---

### `fan-arrows-downward.png` → `shapes/compound/`
**What it shows:** An X mark at top center, with 5 curved lines radiating downward and outward, each ending in an arrowhead. CONFIRMED match for existing _core.md fan-arrows shape — this is the canonical reference image.
**Use when:** One input → many outputs, leverage, distribution, one skill applied broadly.
**Note:** The arrows fan downward (from X at top → outward to bottom). The existing _core.md snippet has arrows going upward from origin — update/confirm direction based on this image. In this reference, origin (X) is at top and arrows radiate DOWN and OUT.
**SVG snippet:** See _core.md — adjust Y direction so origin is at top.

---

### `bars-ascending-staircase.png` → `shapes/lines/`
**What it shows:** ~7 thin vertical bars arranged diagonally ascending from bottom-left to top-right, each slightly taller than the previous. Like a staircase or ascending candlestick chart. The progression goes: short → tall, left → right.
**Use when:** Incremental growth, compounding steps, daily progress, ladder of improvement.
**Animation pattern:** Bars grow from baseline upward one at a time with stagger (scaleY from 0 to 1, transformOrigin bottom).
**Key patterns:** Bars are thin (~4px wide). Heights increase roughly 15–20% per step. Baseline is shared. No connecting line — each bar stands alone.
**SVG snippet:**
```svg
<!-- 7 bars, ascending, staggered from left -->
<line x1="350" y1="650" x2="350" y2="590" stroke="white" stroke-width="4"/>
<line x1="370" y1="650" x2="370" y2="575" stroke="white" stroke-width="4"/>
<line x1="390" y1="650" x2="390" y2="558" stroke="white" stroke-width="4"/>
<line x1="410" y1="650" x2="410" y2="537" stroke="white" stroke-width="4"/>
<line x1="430" y1="650" x2="430" y2="512" stroke="white" stroke-width="4"/>
<line x1="450" y1="650" x2="450" y2="482" stroke="white" stroke-width="4"/>
<line x1="470" y1="650" x2="470" y2="446" stroke="white" stroke-width="4"/>
```

---

### `curve-spike-vs-flat.png` → `shapes/compound/`
**What it shows:** Left: a curve that starts flat/horizontal, rises in a tight exponential arc to a sharp peak, then drops vertically back down (spike pattern). Right: a simple flat horizontal line at the same baseline. Variant of the growth-curve-comparison — this version emphasizes a sharp single spike vs sustained flatness.
**Use when:** Viral moment vs consistent work, one-hit vs long game, luck vs skill, burst vs baseline.
**Key patterns:** The spike is very tight — narrow peak, steep rise and fall. The flat line is at the same baseline height as the start of the spike curve. Total width is roughly split 40/60 left/right.
**SVG snippet:**
```svg
<!-- Spike curve: flat start, tight exponential rise, vertical drop -->
<path d="M 100,540 L 280,540 C 320,540 340,460 360,400 C 370,350 380,330 390,310
  L 390,540" fill="none" stroke="white" stroke-width="1.5"/>
<!-- Flat line (right) -->
<line x1="440" y1="540" x2="720" y2="540" stroke="white" stroke-width="1.5"/>
```

---

## Shapes confirmed from Batch 1 (already in _core.md)
- input-into-process ✓
- fan-arrows-one-to-many ✓ (direction: top origin → arrows down)
- vertical-bars-comparison ✓ (EARN/SPEND labels)
- growth-curve-comparison ✓ (spike variant documented above)

## New shapes to add to _core.md
- circle-merge-sequence (Venn merger animation)
- circle-bright-vs-dim (opacity states for the ball)
- arrow-x-emphasis-swap (dim/bright state inversion)
- rect-frame-signal-noise (framing as focus)
- bars-ascending-staircase (step growth)
- curve-spike-vs-flat (spike variant)
- content-density-scale (line → stack → grid)

---
<!-- Batch 1: 16 images · 7 new shapes · 4 confirmations · 5 layouts/compound -->

---

## Batch 2 — Full Inbox Sort (95 files)

All files copied from `inbox/` to `vv-style/` subfolders. Entries organized by destination subfolder.

---

## shapes/circles/

### `circle-merge-sequence.png` → `shapes/circles/`
**What it shows:** Four-state sequence of two circles merging: hollow ring alone → hollow + solid overlapping slightly → two circles deeply overlapping (intersection region fills dark) → single solid circle with ring outline.
**Use when:** Integration, collaboration, two things becoming one, overlap revealing shared value.
**Key patterns:** Thin stroke (~1.5px). The dark lens at step 3 shows intersection. Final circle retains ring stroke.

---

### `circle-radial-spokes-halves.png` → `shapes/circles/`
**What it shows:** A circle divided by radial spokes into halves or wedges. Like a pie split into equal sections with spokes radiating from center.
**Use when:** Equal division, proportional shares, splitting resources or time.
**Key patterns:** Spokes thin, uniform stroke. Circle outline present.

---

### `circle-single-small-centered.png` → `shapes/circles/`
**What it shows:** A single small hollow circle centered on the canvas. Minimal, isolated.
**Use when:** The self, a point, a dot in a system. Foundational starting state.
**Key patterns:** Radius ~30–40px. Thin stroke. No glow.

---

### `circle-separate-to-one-progression.png` → `shapes/circles/`
**What it shows:** Four-state sequence of four separate circles collapsing into one: 4 apart → 3 apart → 2 overlapping → 1 merged circle.
**Use when:** Consolidation, focus, narrowing from many options to one, team coming together.
**Key patterns:** Each state equally spaced horizontally. Final state is single solid or outlined circle.

---

### `circles-nested-fractal-large-small.png` → `shapes/circles/`
**What it shows:** A large circle containing a smaller concentric circle inside, possibly with another layer — fractal nesting.
**Use when:** Systems within systems, the macro containing the micro, scale relationships.
**Key patterns:** Both outlines thin. Centered. No fill.

---

### `circles-two-bright-vs-dim.png` → `shapes/circles/`
**What it shows:** Two circles side by side — left bright white, right low opacity (~15–20%). Same size, same stroke.
**Use when:** Seen vs unseen, known vs unknown, active vs inactive, before/after brightness.
**Key patterns:** Opacity difference is the entire message. Identical geometry.

---

### `circle-pie-said-vs-done.png` → `shapes/circles/`
**What it shows:** A pie chart divided into two unequal slices labeled SAID and DONE. SAID is the larger portion, DONE is smaller.
**Use when:** Gap between intention and execution, talk vs action, promises vs delivery.
**Key patterns:** Simple two-slice pie, small caps labels. The imbalance is the point.

---

### `circles-concentric-x-marks-focusing.png` → `shapes/circles/`
**What it shows:** Three concentric bullseye rings with X marks at various positions, narrowing toward center — showing targeting or focusing progression.
**Use when:** Narrowing focus, honing in on a goal, precision improving over time.
**Key patterns:** Three rings, X marks moving from outer to inner across states.

---

### `circles-three-arc-completion.png` → `shapes/circles/`
**What it shows:** Three circles in a row showing arc-to-full-circle progression: partial arc → larger arc → complete circle.
**Use when:** Completion, progress toward wholeness, a process finishing.
**Key patterns:** Thin stroke. Arc gaps close progressively left to right.

---

### `circle-full-vs-arc-with-dot.png` → `shapes/circles/`
**What it shows:** Two states side by side: a complete solid or outline circle vs a partial arc with a dot at the open end.
**Use when:** Complete vs incomplete, closed vs open, done vs in progress.
**Key patterns:** The dot at arc tip suggests a moving point or incomplete draw.

---

## shapes/rectangles/

### `rect-open-with-stem.png` → `shapes/rectangles/`
**What it shows:** An open rectangle (three sides: top, right, bottom — left side open) with a short stem extending left from the open edge.
**Use when:** Input channel, funnel entry, a process receiving something from the left.
**Key patterns:** Three-sided rect = open system. Stem on left = incoming element.

---

### `rects-nested-dark-to-white-center.png` → `shapes/rectangles/`
**What it shows:** Concentric squares going from dark/dim outer to bright/white center. Nested rectangles creating a tunnel or focus effect.
**Use when:** Depth, focus pulling to center, layered containment, zooming in.
**Key patterns:** Each nested rect brighter than the previous. Thin strokes.

---

### `progress-bar-grids-six-variants.png` → `shapes/rectangles/`
**What it shows:** Six horizontal segmented/grid bars showing different fill states — empty, partial, full in various proportions.
**Use when:** Reference for all fill-state variations of a segmented progress bar.
**Key patterns:** Each bar divided into equal cells. White fill from left. Thin stroke.

---

### `progress-bars-full-vs-partial-groups.png` → `shapes/rectangles/`
**What it shows:** Two groups of four bars each — one group showing full/complete bars, another showing partial fill.
**Use when:** Comparing two states of capacity, showing before and after fill, contrasting completion rates.
**Key patterns:** Groups of 4 stacked bars. Fill contrast between groups is the message.

---

### `rect-large-frame-small-segmented-bar.png` → `shapes/rectangles/`
**What it shows:** A large portrait or landscape frame outline with a small segmented progress bar inside or below it.
**Use when:** Content frame with a progress indicator, showing how much of something is complete.
**Key patterns:** Large rect = container. Small bar = progress/fill indicator within.

---

### `rect-subdividing-more-cells.png` → `shapes/rectangles/`
**What it shows:** A rectangle that subdivides into more and more cells across states — showing growing granularity or complexity within the same container.
**Use when:** Breaking a whole into parts, granularity increasing, one becoming many.
**Key patterns:** Same outer rect. Interior grid lines multiply across states.

---

### `rects-bars-filling-capacity-arrows.png` → `shapes/rectangles/`
**What it shows:** Three horizontal bars with downward-pointing capacity arrows above or beside them, indicating different fill levels.
**Use when:** Capacity utilization, headroom remaining, filling toward a limit.
**Key patterns:** Downward arrows indicate the fill direction or capacity marker.

---

### `capsule-bars-three-fill-states.png` → `shapes/rectangles/`
**What it shows:** Three pill/capsule-shaped bars (rounded ends) showing three different fill states — low, medium, high.
**Use when:** Progress indicator variants, loading states, capacity at different levels.
**Key patterns:** Rounded rx ends. White fill from left at different widths.

---

## shapes/triangles/

### `triangle-grow-sequence.png` → `shapes/triangles/`
**What it shows:** A sequence of triangles growing in size from left to right, all sharing the same baseline.
**Use when:** Growth, scaling up, the expanding triangle of compound returns.
**Key patterns:** All triangles outline only. Same baseline. Uniform thin stroke.

---

### `triangle-outline-vs-grid-filled.png` → `shapes/triangles/`
**What it shows:** Two triangles side by side: left is a clean outline triangle, right is the same shape filled with a geodesic dot grid or small triangle subdivisions.
**Use when:** Simple vs complex, empty vs full, structure vs content.
**Key patterns:** Same triangle shape, same size. The interior detail of the right is the contrast.

---

## shapes/lines/

### `bars-chasing-having-losing.png` → `shapes/lines/`
**What it shows:** Three pairs of vertical bars labeled CHASING, HAVING, LOSING — showing three emotional/state phases with different bar height ratios in each pair.
**Use when:** Lifecycle of desire, goal pursuit phases, before/during/after achieving something.
**Key patterns:** Three groups. Small caps labels. Vertical bar heights vary per group.

---

### `lines-two-horizontal-bright-dim.png` → `shapes/lines/`
**What it shows:** Two horizontal lines — one bright white, one dim/low-opacity. Same length.
**Use when:** Signal vs noise, the important vs the background, what to focus on vs what to ignore.
**Key patterns:** Identical geometry, opacity is the only difference.

---

### `lines-two-horizontal-length-contrast.png` → `shapes/lines/`
**What it shows:** Two horizontal lines of very different lengths — one long, one short. Side by side for comparison.
**Use when:** Big vs small, the scale difference between two things, magnitude comparison.
**Key patterns:** Both same stroke weight. Length ratio is the message.

---

### `line-circles-small-large-on-axis.png` → `shapes/lines/`
**What it shows:** A horizontal axis line with two circles on it — one small, one large — positioned at different points.
**Use when:** Scale comparison on a timeline or axis, small now vs large later, a journey with different sized moments.
**Key patterns:** Thin axis line. Circles are outline. Size difference is significant.

---

### `lines-one-to-grid-progression.png` → `shapes/lines/`
**What it shows:** Three-state progression: single dash → three stacked lines → hash/grid pattern. Content density scaling.
**Use when:** One idea → list → system, information density growing, simplicity becoming complexity.
**Key patterns:** Uniform stroke weight. Each state wider than the previous.

---

### `line-single-gradient-horizontal.png` → `shapes/lines/`
**What it shows:** A single horizontal line that fades from bright to dim (gradient effect) left to right or center outward.
**Use when:** Something fading, trail effect, attention decreasing, signal weakening.
**Key patterns:** Gradient or opacity fade. Single line. Thin stroke.

---

### `vertical-lines-dots-scatter-to-outlier.png` → `shapes/lines/`
**What it shows:** Five vertical lines in a cluster plus one outlier dot positioned separately — showing the exceptional vs the group.
**Use when:** The outlier, the one that breaks the pattern, statistical anomaly, standing apart.
**Key patterns:** Group of 5 tight lines, one dot far from the group.

---

### `lines-vertical-tall-vs-short-time-attention.png` → `shapes/lines/`
**What it shows:** Two vertical lines — one tall, one short — with small icons or labels indicating TIME and ATTENTION axes.
**Use when:** Time vs attention tradeoff, long duration vs short attention span.
**Key patterns:** Tall vs short contrast. Labels or icons at base or top.

---

### `vertical-lines-group-vs-constrained.png` → `shapes/lines/`
**What it shows:** Three free-standing vertical lines vs two vertical lines constrained within brackets or bounds.
**Use when:** Freedom vs constraint, open vs bounded, free agent vs structure.
**Key patterns:** Left group has no boundaries. Right group has enclosing marks.

---

### `line-solid-vs-dotted-pair.png` → `shapes/lines/`
**What it shows:** A solid horizontal line paired with a dashed/dotted horizontal line.
**Use when:** Actual vs projected, real vs estimated, present vs future.
**Key patterns:** Same length. Solid = certain, dotted = uncertain/projected.

---

### `curve-bell-normal-distribution.png` → `shapes/lines/`
**What it shows:** A bell curve (normal distribution) with the left tail highlighted or emphasized differently.
**Use when:** Distribution of outcomes, average vs outlier, the long tail, bell curve arguments.
**Key patterns:** Smooth bell curve. Left tail distinction. Thin stroke.

---

### `vertical-ticks-growing-sequence.png` → `shapes/lines/`
**What it shows:** Six vertical tick marks growing progressively taller from left to right — like a bar chart or staircase made of individual tick lines.
**Use when:** Sequential growth, daily consistency building, incremental progress over time.
**Key patterns:** Thin strokes. Heights increase ~20% per step. Evenly spaced.

---

### `lines-wave-bundle-v-shape.png` → `shapes/lines/`
**What it shows:** Multiple lines bundled together forming a V-shape or wave pattern — lines converging from both sides to a low point then rising.
**Use when:** Valley between two peaks, the dip before recovery, the trough.
**Key patterns:** Multi-line bundle. V-shape path. Lines parallel within the bundle.

---

## shapes/compound/

### `symbol-plus-vs-x.png` → `shapes/compound/`
**What it shows:** A plus (+) sign and an X (×) sign side by side — the two fundamental operators, addition vs cancellation/multiplication.
**Use when:** And vs not, combine vs remove, add vs multiply, yes vs no.
**Key patterns:** Same stroke weight for both symbols. Clean geometric construction.

---

### `diamond-stack-compounding.png` → `shapes/compound/`
**What it shows:** A stack of diamond shapes growing upward, representing compounding layers or accumulating value.
**Use when:** Compounding returns, layered value, each period building on the last.
**Key patterns:** Diamonds stacked vertically. Each layer adds to the total height.

---

### `tube-rings-scatter.png` → `shapes/compound/`
**What it shows:** Circular rings scattered around or emanating from a tube/cylinder shape — showing signal broadcast, emission, or spread.
**Use when:** Broadcasting, influence spreading, signals going out from a source.
**Key patterns:** Cylinder/tube form as source. Rings at various angles around it.

---

### `symbol-x-to-dot-sequence.png` → `shapes/compound/`
**What it shows:** A sequence showing an X mark transforming into a dot — from wrong/close to a point/precise.
**Use when:** Narrowing, error becoming pinpoint, from rejection to precision.
**Key patterns:** X large → shrinks → becomes dot. Linear progression.

---

### `fan-arrows-from-x.png` → `shapes/compound/`
**What it shows:** An X mark at top center with 5 curved lines radiating downward and outward as arrows — one-to-many distribution.
**Use when:** One idea → many applications, leverage, distribution, one skill applied broadly.
**Key patterns:** Origin at top (X). Arrows fan downward and outward. Curved lines with arrowheads.

---

### `symbol-percent-greater-hash.png` → `shapes/compound/`
**What it shows:** Three symbols in a row: % (percent), > (greater than), # (hash/number). Shows a hierarchy or comparison of these operators.
**Use when:** Percentage beats absolute number, rate beats count, relative vs absolute.
**Key patterns:** Three symbols, same size, evenly spaced. Clean geometric forms.

---

### `columns-x-to-check-conversion.png` → `shapes/compound/`
**What it shows:** Five vertical columns each showing an X transforming into a checkmark — conversion or correction happening across multiple items simultaneously.
**Use when:** Batch correction, fixing multiple problems at once, systematic improvement.
**Key patterns:** 5 columns, each showing X→check. Parallel transformation.

---

### `arrow-point-progress-bar-one-step.png` → `shapes/compound/`
**What it shows:** A chevron/arrow pointer paired with a segmented progress bar showing only one cell filled — the very first step taken.
**Use when:** Beginning a journey, one step done, starting momentum.
**Key patterns:** Chevron indicates direction. One-cell fill = minimal progress = start.

---

### `symbol-speaker-volume-to-mute.png` → `shapes/compound/`
**What it shows:** Three states: speaker icon → megaphone icon → mute/X icon. Volume escalating then silenced.
**Use when:** Communication arc, amplification turning off, reach then silence.
**Key patterns:** Three states. Icons simple and geometric.

---

### `row-circled-checkmarks.png` → `shapes/compound/`
**What it shows:** Six circled checkmarks in a horizontal row — items verified, steps completed, checklist finished.
**Use when:** All boxes checked, completion, six-step process finished, full verification.
**Key patterns:** Each checkmark enclosed in a circle. Evenly spaced row.

---

### `circles-cluster-cross-pattern.png` → `shapes/compound/`
**What it shows:** Six circles arranged in a cross/plus formation (top, bottom, left, right, center + one more) plus a small signature or mark.
**Use when:** Network hub with four directions, cardinal points, a central node with four connections.
**Key patterns:** Cross formation. Six circles. Uniform size and stroke.

---

### `arrows-collapse-vs-expand.png` → `shapes/compound/`
**What it shows:** Two groups of arrows: one with arrows pointing inward (collapsing/converging) vs one with arrows pointing outward (expanding/diverging).
**Use when:** Focus vs distribution, contraction vs expansion, gather vs spread.
**Key patterns:** Arrow directions are the message. Both groups similar in scale.

---

### `line-circles-small-large-on-axis.png` → `shapes/compound/`
**What it shows:** A horizontal axis with a small circle and a large circle positioned at different points on it.
**Use when:** Scale comparison over time or space, small beginning vs large end.
**Key patterns:** Axis line thin. Circles outline only. Size contrast significant.

---

### `diagonal-staircase-compound-growth.png` → `shapes/compound/`
**What it shows:** A diagonal line rising from bottom-left to top-right with nodes at intervals and curved arcs between nodes — compound growth path.
**Use when:** Compounding returns, non-linear growth with distinct steps, the staircase of compound interest.
**Key patterns:** Diagonal line. Nodes (dots or circles) at step points. Curved arcs between.

---

### `circle-solid-vs-dot-grid.png` → `shapes/compound/`
**What it shows:** Left: large solid white circle. Right: 6×6 dot grid. Concentration vs distribution.
**Use when:** One vs many, singular vs plural, mass vs network.
**Key patterns:** Solid circle visually dominant. Dot grid = 36 points at 20px spacing.

---

### `curve-spike-vs-flat-line.png` → `shapes/compound/`
**What it shows:** Left: exponential spike curve (flat → sharp peak → vertical drop). Right: flat horizontal line at same baseline.
**Use when:** Viral vs consistent, burst vs sustained, luck vs skill.
**Key patterns:** Spike is tight and narrow. Flat line at same baseline height.

---

### `maze-with-solution-path.png` → `shapes/compound/`
**What it shows:** A maze pattern with a white highlighted solution path showing the route through.
**Use when:** Finding the path through complexity, the solution within the problem, navigation.
**Key patterns:** Maze in dim lines. Solution path in bright white. Single clear route.

---

### `ellipses-concentric-arrow-rising.png` → `shapes/compound/`
**What it shows:** Flat concentric ellipses (like a target seen from an angle) with an upward arrow rising from center.
**Use when:** Rising above the average, breaking out from the norm, upward trajectory from a central point.
**Key patterns:** Ellipses flat/oblique perspective. Arrow vertical, rising from center ring.

---

### `cards-stacked-isometric-play-code.png` → `shapes/compound/`
**What it shows:** Two isometric cards stacked at an angle — one showing a play button, one showing code brackets or similar.
**Use when:** Layered content, media vs code, two formats of the same idea.
**Key patterns:** Isometric perspective. Two cards at offset angles.

---

### `bar-chart-3d-isometric.png` → `shapes/compound/`
**What it shows:** A single 3D isometric bar on a floor plane — like a column rising from a grid surface.
**Use when:** One metric, a single bar chart, isolated data point in 3D space.
**Key patterns:** Isometric perspective. Floor grid. Single bar with top face.

---

### `arrows-radial-from-center.png` → `shapes/compound/`
**What it shows:** 10+ arrows radiating outward from a center point in all directions — 360° distribution.
**Use when:** Influence spreading in all directions, broadcast, explosion of outputs from one source.
**Key patterns:** All arrows same length. Uniform angles. Center origin.

---

### `cube-small-vs-obelisk-tall.png` → `shapes/compound/`
**What it shows:** A small cube next to a tall thin obelisk/column — contrasting compact vs elongated forms.
**Use when:** Width vs height, breadth vs depth, compact vs reaching.
**Key patterns:** Both outline 3D shapes. Same base width approximately. Height contrast is extreme.

---

### `grid-squares-circle-outlier.png` → `shapes/compound/`
**What it shows:** A 3×3 grid of squares with one circle replacing one square — the odd one out.
**Use when:** The outlier, non-conformity, one different element in a uniform set.
**Key patterns:** 8 squares + 1 circle. Same grid positions. The circle breaks the pattern.

---

### `chart-volatile-framed-window.png` → `shapes/compound/`
**What it shows:** A volatile jagged chart line with a rectangular frame overlaid on a portion — the frame crops/focuses on a section of the noise.
**Use when:** Signal vs noise, what you choose to measure, framing the data that suits your narrative.
**Key patterns:** Full volatile line dim. Frame bright. Inside-frame portion highlighted.

---

### `speech-bubble-with-declining-chart.png` → `shapes/compound/`
**What it shows:** A speech bubble containing a declining chart line — words containing a downward trend.
**Use when:** What's being said is declining, talk that reveals a falling narrative, promises vs reality.
**Key patterns:** Speech bubble outline. Chart inside going down-right.

---

### `speech-bubbles-nine-directions.png` → `shapes/compound/`
**What it shows:** Nine speech bubbles each with an arrow pointing in a different direction — showing all possible communication vectors.
**Use when:** Multi-directional conversation, nine states of dialogue, choosing which direction to send a message.
**Key patterns:** 3×3 grid of bubbles. Each has a different tail direction.

---

### `grid-square-vs-diamond-gem.png` → `shapes/compound/`
**What it shows:** A 3×3 grid of squares vs a faceted diamond/gem shape — structured data vs crystallized value.
**Use when:** Raw vs refined, information vs insight, commodity vs gem.
**Key patterns:** Grid is flat/regular. Gem has multiple facet lines creating depth.

---

### `arrows-up-growing-with-x-caps.png` → `shapes/compound/`
**What it shows:** Four upward arrows of increasing height, each capped with an × mark at the top.
**Use when:** Growth that gets stopped, attempts that fail at increasing scale, trying harder but hitting a ceiling.
**Key patterns:** Arrows grow taller left to right. × caps all at same position relative to arrow tip.

---

### `symbol-infinity-with-location-pin.png` → `shapes/compound/`
**What it shows:** An infinity symbol (∞) with a location pin/marker overlaid at a specific point on the loop.
**Use when:** Where you are in an infinite loop, your position in an endless cycle, the specific point that matters.
**Key patterns:** Infinity symbol outline. Pin at intersection or specific point on loop.

---

### `network-hub-spoke-vs-full-mesh.png` → `shapes/compound/`
**What it shows:** Two network diagrams: left is hub-and-spoke (all connected to center), right is full mesh (all connected to all).
**Use when:** Centralized vs decentralized, single point of failure vs redundancy, hierarchy vs network.
**Key patterns:** Hub-spoke: 1 center + 4-6 outer nodes. Full mesh: all nodes directly connected.

---

### `circle-x-inside-with-smaller-circles.png` → `shapes/compound/`
**What it shows:** A large circle containing an X mark inside, surrounded by smaller circles — like a thought bubble with a rejected idea.
**Use when:** Wrong answer surrounded by possibilities, rejecting the obvious, the X in the system.
**Key patterns:** Large circle main. X inside. Smaller circles orbiting or adjacent.

---

### `wave-oscillating-around-trend-line.png` → `shapes/compound/`
**What it shows:** A sine wave oscillating above and below a flat trend line, labeled TRUTH and TREND — showing how perception fluctuates around reality.
**Use when:** Market fluctuations around value, mood vs reality, noise around signal.
**Key patterns:** Sine wave in brighter white. Trend line thinner/dimmer. Labels TRUTH/TREND.

---

### `circle-dashed-vs-spike-curve-noise-signal.png` → `shapes/compound/`
**What it shows:** A dashed ring vs a spike/jagged curve — the smooth ideal vs the noisy reality.
**Use when:** Expected vs actual, model vs data, clean signal vs noisy output.
**Key patterns:** Dashed circle = theoretical. Spike curve = empirical noise.

---

### `circle-rotation-vs-arrow-direction.png` → `shapes/compound/`
**What it shows:** A circular rotation indicator vs a straight directional arrow — circular motion vs linear direction.
**Use when:** Cycle vs journey, recurring vs one-time, rotation vs progression.
**Key patterns:** Rotation circle has curved arrows. Direction arrow is straight.

---

### `hearts-three-sizes-with-people-counter.png` → `shapes/compound/`
**What it shows:** Three hearts of increasing size with a people counter or number — showing audience size correlating with heart/love scale.
**Use when:** Audience growth, likes/engagement scaling, love growing with reach.
**Key patterns:** Three hearts small/medium/large. Number counter alongside each.

---

### `arrows-parallel-diagonal-fan.png` → `shapes/compound/`
**What it shows:** Six parallel diagonal arrows all pointing the same direction — a fan or bundle of arrows moving together.
**Use when:** Collective movement, all pointing the same way, momentum, aligned force.
**Key patterns:** Arrows parallel, not converging. Diagonal orientation (~45°).

---

### `circle-8-arrows-bright-vs-dim.png` → `shapes/compound/`
**What it shows:** A circle with 8 arrows in two brightness states — some arrows bright white, some dim — showing selective direction emphasis.
**Use when:** Choosing a direction from many, highlighting one path among options, focus from a radial set.
**Key patterns:** 8 arrows at 45° intervals. Two brightness levels: bright (selected) and dim (available).

---

### `speech-bubbles-grid-progress-bars.png` → `shapes/compound/`
**What it shows:** 18 speech bubbles arranged in a grid, each containing a small progress bar — showing conversation volume with completion states.
**Use when:** Many conversations, task progress across multiple items, communication load.
**Key patterns:** 18 bubbles in grid. Each has internal progress bar at varying fill levels.

---

## movements/

### `diagonal-staircase-compound-growth.png` → `movements/`
**What it shows:** A diagonal rising line with nodes and arcs showing compound growth steps — the staircase pattern of exponential progression.
**Use when:** Compounding returns, non-linear growth with distinct accumulation steps.
**Key patterns:** Diagonal line + nodes + curved arcs between nodes.

---

### `staircase-steps-ascending.png` → `movements/`
**What it shows:** A staircase line rising from bottom-left to top-right in discrete steps — each step horizontal then vertical.
**Use when:** Incremental progress, step-by-step growth, deliberate ascent.
**Key patterns:** Right-angle steps. Each step equal width and height.

---

### `spiral-curl-to-arrow-path.png` → `movements/`
**What it shows:** A curling spiral path that straightens into a bright directional arrow — confusion resolving into direction.
**Use when:** Finding your way, clarity emerging from chaos, the winding path becoming direct.
**Key patterns:** Spiral dim → arrow bright. Path continues from spiral into straight arrow.

---

### `spiral-cone-widening.png` → `movements/`
**What it shows:** A tight spiral that widens outward — like a cone or expanding helix.
**Use when:** Options expanding over time, knowledge base widening, cone of uncertainty.
**Key patterns:** Tight center → loose outer rings. Cone shape overall.

---

## layouts/

### `layout-price-vs-value-fork.png` → `layouts/`
**What it shows:** A fork/branch diagram showing PRICE diverging from VALUE over time or at a decision point.
**Use when:** Price and value decoupling, mispriced asset, the gap between what something costs and what it's worth.
**Key patterns:** Fork from single line into two diverging paths. Labels PRICE / VALUE.

---

### `layout-linear-vs-exponential-numbers.png` → `layouts/`
**What it shows:** Two columns of numbers — left showing odd-number linear progression, right showing doubling (exponential). The contrast shows how fast compounding grows vs linear growth.
**Use when:** Why compounding wins, linear thinking vs exponential reality.
**Key patterns:** Numbers aligned in columns. Exponential right column numbers grow rapidly.

---

### `layout-person-idea-grows-sequence.png` → `layouts/`
**What it shows:** Three states of a person with a speech bubble/idea, each state showing a growing triangle below — the idea's impact expanding.
**Use when:** Idea maturity, an insight growing its reach, thought becoming influence.
**Key patterns:** Person icon stable. Bubble stable. Triangle grows across three states.

---

### `layout-truth-three-representations.png` → `layouts/`
**What it shows:** Three different icon representations of the same concept all labeled TRUTH — showing that truth can take multiple forms.
**Use when:** Multiple expressions of one reality, same thing different views.
**Key patterns:** Three icons, one label TRUTH repeated. Small caps.

---

### `layout-polygon-evolving-to-circle.png` → `layouts/`
**What it shows:** A polygon with many sides evolving toward a perfect circle, with text labels marking the progression.
**Use when:** Iteration toward perfection, rough edges smoothing, process maturity.
**Key patterns:** Polygon → circle. Labels below each state. Same size throughout.

---

### `layout-complexity-to-simplicity-versioning.png` → `layouts/`
**What it shows:** V.1 showing a chaotic fragmented grid vs V.674 showing a single clean rectangle — radical simplification over iterations.
**Use when:** Design refinement, editing as mastery, removing until nothing is left to remove.
**Key patterns:** Fragmented squares left. Single clean rect right. Version numbers small.

---

### `layout-letters-checked-spell-understanding.png` → `layouts/`
**What it shows:** Individual letters with checkmarks below each, spelling out UNDERSTANDING — showing building comprehension letter by letter.
**Use when:** Building knowledge piece by piece, spelling out mastery, systematic learning.
**Key patterns:** Letters + checks in grid. Spells meaningful word when complete.

---

### `layout-earn-vs-spend-bars-two-states.png` → `layouts/`
**What it shows:** EARN and SPEND bars shown in two states: equal (break-even) and EARN > SPEND (surplus). Labels below in small caps.
**Use when:** Financial health, surplus vs deficit, the goal state vs break-even.
**Key patterns:** Vertical bars. Small caps labels. Two side-by-side comparison groups.

---

### `layout-truth-bias-perception-spotlight.png` → `layouts/`
**What it shows:** A spotlight illuminating different portions — TRUTH, BIAS, and PERCEPTION labeled within the light cone.
**Use when:** How selective attention shapes what we call truth, bias filtering perception.
**Key patterns:** Spotlight cone shape. Labels within illuminated area.

---

### `layout-invoice-skill-vs-knowledge.png` → `layouts/`
**What it shows:** An invoice-style layout with two line items: skill at $1 and knowledge at $9,999 (or similar dramatic contrast).
**Use when:** Execution beats information, knowing vs doing, the value gap between learning and applying.
**Key patterns:** Invoice format. Two items. Price contrast is extreme and deliberate.

---

### `layout-done-vs-perfect-text-only.png` → `layouts/`
**What it shows:** Text-only composition: "DONE" on one side, "P" (for PERFECT, truncated) on the other — DONE wins by being complete.
**Use when:** Shipping beats perfecting, done > perfect, execution over polish.
**Key patterns:** All caps. Wide spacing. Text only — no shapes.

---

### `layout-multiply-zero-vs-add-one.png` → `layouts/`
**What it shows:** Two equations: 0 × 10 = 0 (left) and 0 + 1 = 1 (right) — starting from nothing, multiplication of zero gives nothing, but adding one gives one.
**Use when:** Starting > optimizing nothing, one unit of progress beats infinite multiplication of zero.
**Key patterns:** Equation format. Large numbers. Minimal sans typography.

---

### `layout-vertical-text-reading-investment.png` → `layouts/`
**What it shows:** Text rotated vertically that reads INVESTMENT or a related word — requiring the viewer to tilt their head, making them work for the read.
**Use when:** Investment requires effort to understand, the message about commitment delivered through form.
**Key patterns:** Rotated 90° text. Single word. No other elements.

---

### `layout-xp-points-list.png` → `layouts/`
**What it shows:** A list format with XP values beside items — like an RPG experience points scoreboard for real-world activities.
**Use when:** Gamification of learning, life as a game, quantifying intangible progress.
**Key patterns:** Left-aligned labels. Right-aligned numbers. Monospaced or tabular format.

---

### `layout-pyramid-needs-wants-vibes.png` → `layouts/`
**What it shows:** A triangle/pyramid with three horizontal levels labeled NEEDS (bottom), WANTS (middle), VIBES (top).
**Use when:** Hierarchy of motivations, Maslow-like structure, what drives decisions at different levels.
**Key patterns:** Triangle outline. Three horizontal divisions. Small caps labels per tier.

---

### `layout-million-vs-one-second.png` → `layouts/`
**What it shows:** Two large typographic elements: 1,000,000 on one side and 00:00:01 on the other — a million of something vs one second.
**Use when:** Scale contrast, the value of attention vs the abundance of something else, time as the scarce resource.
**Key patterns:** Large numbers. Contrasting formats (comma-separated vs timer). No other elements.

---

### `layout-jpg-vs-nft-rectangles.png` → `layouts/`
**What it shows:** Two identical rectangles labeled JPG and NFT — one with a verification badge. Same object, different provenance.
**Use when:** How context changes value, the role of authentication, identical things with different meaning.
**Key patterns:** Two landscape rects. Labels inside. One has a badge (color exception in otherwise B&W library).

---

## effects/

### `glow-blur-to-focus.png` → `effects/`
**What it shows:** A progression from blurred/glowing state to sharp focused state — the same element going from soft to crisp.
**Use when:** Clarity emerging, focus arriving, something coming into view.
**Key patterns:** Gaussian blur decreasing. Glow reducing. Same shape throughout.

---

### `dots-circle-density-progression.png` → `effects/`
**What it shows:** A circle made of dots, showing density increasing — from sparse dots to dense dot circle.
**Use when:** Accumulation, density building, a form emerging from particles.
**Key patterns:** Same circle radius. Dot count increases per state. Dots are small circles.

---

### `dots-pairs-opacity-fade.png` → `effects/`
**What it shows:** Three pairs of dots, each pair fading in opacity — showing signal decay or distance fade.
**Use when:** Diminishing signal, fading over time, trailing dots, echo effect.
**Key patterns:** Three pairs. Each pair dimmer than the previous. Uniform dot size.

---

### `blur-rects-circle-focus-center.png` → `effects/`
**What it shows:** Blurred rectangles surrounding a sharp, clearly-rendered circle at center — peripheral blur with center focus.
**Use when:** Attention narrowing to a single point, depth of field effect, everything else falling away.
**Key patterns:** Outer rects blurred/dim. Center circle crisp white. Depth illusion.

---

---

### `progress-bars-fill-states.png` → `shapes/rectangles/`
**What it shows:** Three horizontal landscape progress bars side by side — each showing a different fill level. Left: ~90% solid fill with small outline gap at right. Middle: ~50% fill. Right: ~10% fill (mostly outline). Black background, white fill.
**Use when:** Showing completion, capacity, ratio, or a metric filling up over time. Three-state sequence suggests animation frames.
**Key patterns:** Landscape rect split into solid-fill portion + outline-only portion. Fill slides left-to-right. Width ~160px, height ~18px per bar.
```svg
<!-- Progress bar: outline container + fill rect -->
<rect x="80" y="350" width="160" height="18" fill="none" stroke="white" stroke-width="1.5"/>
<rect id="fill" x="80" y="350" width="144" height="18" fill="white"/> <!-- 90% fill -->
```

---

## Duplicates Skipped

The following files were skipped (duplicate suffixes " (1)" or " (2)" — identical content):
- All files matching `* (1).png` and `* (2).png` patterns

Total: 9 duplicates skipped, 96 unique files copied.

---
<!-- Batch 2: 96 files · Full inbox sort complete -->
