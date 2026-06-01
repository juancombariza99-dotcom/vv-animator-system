# Core Shape Vocabulary
<!-- Always-loaded reference. Read at the start of any ideate or generate session. -->
<!-- Full images live in references/vv-style/ — load only when visual confirmation needed. -->

---

## The Ball (protagonist)
The ball is in every animation. It represents the mind, person, or idea.

| State | SVG | Meaning |
|-------|-----|---------|
| Hollow ring | `fill="transparent" stroke="white" stroke-width="2"` | Unfulfilled, searching, potential |
| Solid white | `fill="white" stroke="none"` | Formed, active, present |
| Solid + glow | solid fill + `filter="url(#glow)"` | Powerful, landed, complete |
| Tiny dot r=1 | starting state | Not yet formed |

Typical radius: r=1 (dot) → r=26 (full ring/solid) → r=13–16 (small/traveling)

---

## Shapes

### Book (open)
Represents: reading, learning, consuming, input
Structure: spine lines (center) + left page curves + right page curves + baseline
Baseline y ≈ 535 in 405×720 canvas, spanning x 80–270
Draw order: spine → pages fan left+right → baseline
File: `vv-style/shapes/compound/book-open.png`

```svg
<line id="sp1" x1="193" y1="497" x2="193" y2="535" stroke="white" stroke-width="1.3" stroke-dasharray="40" stroke-dashoffset="40"/>
<path id="lp1" d="M 193,505 Q 165,517 105,535" fill="none" stroke="white" stroke-width="1.2" stroke-dasharray="110" stroke-dashoffset="110"/>
<path id="rp1" d="M 193,505 Q 218,517 258,535" fill="none" stroke="white" stroke-width="1.2" stroke-dasharray="110" stroke-dashoffset="110"/>
<line id="b-base" x1="82" y1="535" x2="268" y2="535" stroke="white" stroke-width="1.4" stroke-dasharray="190" stroke-dashoffset="190"/>
```

### Rectangle / Page
Represents: writing, structure, document, articulation
Typical size: 80×185px centered at x=203. Morphs to oval via rx/ry animation.
File: `vv-style/shapes/rectangles/rect-portrait.png`

```svg
<rect id="rect-outline" x="163" y="305" width="80" height="185"
  fill="none" stroke="white" stroke-width="2" opacity="0" rx="0" ry="0"/>
```

### Triangle
Represents: leverage, hierarchy, clarity, direction
Compact size: ~140px wide, ~117px tall, pointing UP
File: `vv-style/shapes/triangles/triangle-up-solid.png`

```svg
<polygon id="triangle" points="203,338 133,455 273,455" fill="white" opacity="0"/>
```

### Horizontal Line
Represents: baseline, foundation, constraint, flatness, no growth
File: `vv-style/shapes/lines/line-horizontal.png`

```svg
<line x1="140" y1="535" x2="264" y2="535" stroke="white" stroke-width="1.4"/>
```

### Vertical Lines (comparison pair)
Represents: two quantities side by side — earn/spend, before/after, with/without
Structure: two vertical lines of different heights, labeled below with small caps text
Use: show ratio or gap between two variables. Taller line = more of that quantity.
Multiple pairs can be shown side by side to compare two states (e.g. surplus vs deficit).
File: `vv-style/shapes/lines/vertical-bars-comparison.png`

```svg
<!-- Example: earn > spend (surplus state) -->
<line x1="160" y1="350" x2="160" y2="510" stroke="white" stroke-width="2"/>  <!-- EARN tall -->
<line x1="200" y1="420" x2="200" y2="510" stroke="white" stroke-width="2"/>  <!-- SPEND short -->
<!-- Labels via .txt divs or SVG <text> below each line -->
```

### Circle (standalone, static)
Represents: idea, loop, cycle, completeness, self
Different from the ball — used as a fixed compositional element, not the moving protagonist.
File: `vv-style/shapes/circles/circle-outline.png`

### Circle Between Two Options
Represents: decision point, the self between two choices, a fork in the road
Structure: hollow circle centered, flanked left and right by two dark rounded-rectangle shapes with soft white glow/halo. Three elements aligned horizontally at center.
The flanking shapes suggest paths, doors, or containers the circle (self) must choose between.
File: `vv-style/shapes/compound/circle-between-options.png`

```svg
<!-- Center circle -->
<circle cx="203" cy="360" r="36" fill="none" stroke="white" stroke-width="2"/>
<!-- Left option (rounded rect with glow — use filter) -->
<rect x="60" y="328" width="100" height="64" rx="12" fill="none" stroke="rgba(255,255,255,0.15)" filter="url(#glow)"/>
<!-- Right option -->
<rect x="245" y="328" width="100" height="64" rx="12" fill="none" stroke="rgba(255,255,255,0.15)" filter="url(#glow)"/>
```

### Growth Curve vs Flat Line
Represents: compound effect, consistency vs stagnation, growth vs no growth
Structure: two shapes side by side.
  Left: a curve that starts flat/horizontal then rises sharply to a peak with a vertical drop line (compound growth shape)
  Right: a simple horizontal flat line (no growth)
The gap between the two end points IS the point.
File: `vv-style/shapes/compound/growth-curve-comparison.png`

```svg
<!-- Compound curve: flat start, exponential rise, vertical peak marker -->
<path d="M 80,480 C 200,478 320,400 360,280" fill="none" stroke="white" stroke-width="1.5"/>
<line x1="360" y1="280" x2="360" y2="480" stroke="white" stroke-width="1.5"/>
<!-- Flat line: same baseline, no growth -->
<line x1="420" y1="480" x2="600" y2="480" stroke="white" stroke-width="1.5"/>
```

### Fan Arrows (one-to-many)
Represents: one input → many outputs, leverage, distribution, one skill applied broadly, reach
Structure: single origin point marked with an X at top center. 5–6 curved lines radiate downward and outward, each ending with an arrowhead. Lines curve gracefully like a spray or fan.
The X marks the source/cause. Arrows mark the effects/destinations.
File: `vv-style/shapes/compound/fan-arrows-one-to-many.png`

```svg
<!-- Origin X mark -->
<line x1="196" y1="218" x2="210" y2="232" stroke="white" stroke-width="1.5"/>
<line x1="210" y1="218" x2="196" y2="232" stroke="white" stroke-width="1.5"/>
<!-- Fan paths — 5 curves from origin fanning outward with endArrow markers -->
<!-- Leftmost -->
<path d="M 203,232 Q 130,350 80,480" fill="none" stroke="white" stroke-width="1.3" marker-end="url(#arrow)"/>
<!-- Center -->
<path d="M 203,232 Q 203,380 203,490" fill="none" stroke="white" stroke-width="1.3" marker-end="url(#arrow)"/>
<!-- Rightmost -->
<path d="M 203,232 Q 276,350 326,480" fill="none" stroke="white" stroke-width="1.3" marker-end="url(#arrow)"/>
<!-- Add 2 more in between for full fan effect -->
```
Note: Define arrowhead marker in `<defs>`. Animate with staggered strokeDashoffset.

### Input into Process (Arrow + Open Box)
Represents: trigger entering a system, attention as input, idea entering a framework, signal → process
Structure: exclamation mark (!) on left + horizontal line feeding into an open-sided rectangle (3 sides: top, right, bottom — open on left). The ! marks the trigger/attention event.
The open-left box suggests a process or container waiting to receive input.
File: `vv-style/shapes/compound/input-into-process.png`

```svg
<!-- Exclamation trigger -->
<line x1="90" y1="320" x2="90" y2="375" stroke="white" stroke-width="2"/>
<circle cx="90" cy="388" r="3" fill="white"/>
<!-- Input arrow line -->
<line x1="95" y1="352" x2="190" y2="352" stroke="white" stroke-width="1.5"/>
<!-- Open-left rectangle (top, right, bottom only) -->
<path d="M 190,305 L 320,305 L 320,400 L 190,400" fill="none" stroke="white" stroke-width="1.5"/>
```

---

## Movements

### Drop and land
Ball falls from top-center, becomes solid on arrival.
- `cy: 250 → 490`, ease: `power1.inOut`, duration: 1.2–1.4s
- On landing: `fill: 'white', filter: 'url(#glow)'`

### Page turn
Left pages fold back (dashoffset reverses), mid-turn arc flashes, right pages close.
- Ball slides LEFT during turn: `cx: 233 → 160`, duration: 0.38s
- Arc flash: opacity 0 → 1 → 0 in ~0.17s total
File: `vv-style/movements/turns/page-turn.png`

### Rect fill + clear
Rectangle fills solid (ball exits right/down), then clears to outline (ball re-enters from right).
- Solid: `rect-solid opacity 0 → 1`, ball exits. Clear: `opacity 1 → 0`, ball returns.

### Rect → oval morph
- `attr: { rx: 40, ry: 92 }`, duration: 0.5s, ease: `power2.inOut`

### Scale up from base
- `scaleY: 0 → 1`, `transformOrigin: '50% 100%'`, ease: `power3.out`

### Scale down from top
- `scaleY: 0 → 1`, `transformOrigin: '50% 0%'`, ease: `power3.out`

### Fan draw-on (staggered)
Animate multiple paths from a single origin using staggered strokeDashoffset.
- Set each path's `stroke-dasharray` = path length
- Stagger: 0.08–0.12s between each line, ease: `power2.out`

---

## Timing conventions
| Event | Duration | Ease |
|-------|----------|------|
| Text fade in | 0.4–0.6s | linear |
| Ball grow from dot | 0.6–0.8s | power2.out |
| Shape draw-on | 0.2–0.45s | power2.out |
| Ball → solid + glow | 0.35–0.45s | power2.out |
| **Hold on scene** | **0.7–1.2s** | — |
| Transition fade | 0.3s | linear |
| Ball travel | 0.35–0.6s | power2.inOut |
| Shape morph | 0.5s | power2.inOut |
| Fan stagger | 0.08–0.12s per line | power2.out |

---

## Glow filter (always include in SVG defs)
```svg
<filter id="glow" x="-50%" y="-50%" width="200%" height="200%">
  <feGaussianBlur stdDeviation="6" result="blur"/>
  <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
</filter>
```

### Circle Merge (two-into-one)
Represents: integration, collaboration, two things becoming one, finding common ground
Animation: Two circles approach from left and right → overlap → intersection fills → one solid circle remains.
File: `vv-style/shapes/circles/circle-merge-sequence.png`

```svg
<!-- Start: two hollow rings at distance -->
<circle id="cA" cx="160" cy="360" r="42" fill="none" stroke="white" stroke-width="1.5"/>
<circle id="cB" cx="250" cy="360" r="42" fill="none" stroke="white" stroke-width="1.5"/>
<!-- End state: single solid circle -->
<circle cx="203" cy="360" r="42" fill="white" stroke="white" stroke-width="1.5"/>
```

### Circle Opacity (dim vs bright)
Represents: unknown vs known, potential vs present, unseen vs visible
Use: fade dim ring up to full brightness — the thing becoming real.
File: `vv-style/shapes/circles/circle-bright-vs-dim.png`

```svg
<circle cx="160" cy="360" r="65" fill="none" stroke="white" stroke-width="1.5"/>             <!-- bright = present -->
<circle cx="310" cy="360" r="65" fill="none" stroke="white" stroke-width="1.5" opacity="0.15"/> <!-- dim = unseen -->
```

### Arrow → X Emphasis Swap
Represents: the relationship between process (arrow) and outcome (X) — which matters more
Use: swap brightness to shift emphasis between doing and result
File: `vv-style/shapes/compound/arrow-x-emphasis-swap.png`

```svg
<!-- Dim arrow, bright X: the outcome is what matters -->
<line x1="160" y1="360" x2="250" y2="360" stroke="rgba(255,255,255,0.35)" stroke-width="1.5"/>
<line x1="272" y1="350" x2="284" y2="370" stroke="white" stroke-width="1.5"/>
<line x1="284" y1="350" x2="272" y2="370" stroke="white" stroke-width="1.5"/>
```

### Rect Frame (signal/noise)
Represents: focus, framing, signal vs noise, attention selecting what matters from chaos
Structure: a continuous zigzag/noisy line runs full width in dim gray; a white rectangle overlays a portion, and inside that frame the same line is drawn in bright white.
File: `vv-style/shapes/compound/rect-frame-signal-noise.png`

```svg
<!-- Full noisy line (dim) -->
<polyline points="80,320 120,390 160,310 200,380 240,300 280,370 320,295 360,365 400,305 440,375"
  fill="none" stroke="rgba(255,255,255,0.25)" stroke-width="1.5"/>
<!-- Rect frame -->
<rect x="195" y="265" width="170" height="210" fill="none" stroke="white" stroke-width="1.5"/>
<!-- Signal: redraw line segment inside rect in white -->
<polyline points="200,380 240,300 280,370 320,295 360,365"
  fill="none" stroke="white" stroke-width="1.5"/>
```

### Ascending Staircase Bars
Represents: incremental growth, compounding steps, daily improvement, building momentum
Animation: bars grow from baseline upward one at a time (staggered scaleY from 0 → 1, transformOrigin bottom)
File: `vv-style/shapes/lines/bars-ascending-staircase.png`

```svg
<!-- 7 bars, ascending left to right, thin width -->
<line x1="340" y1="650" x2="340" y2="596" stroke="white" stroke-width="4"/>
<line x1="360" y1="650" x2="360" y2="579" stroke="white" stroke-width="4"/>
<line x1="380" y1="650" x2="380" y2="560" stroke="white" stroke-width="4"/>
<line x1="400" y1="650" x2="400" y2="538" stroke="white" stroke-width="4"/>
<line x1="420" y1="650" x2="420" y2="513" stroke="white" stroke-width="4"/>
<line x1="440" y1="650" x2="440" y2="484" stroke="white" stroke-width="4"/>
<line x1="460" y1="650" x2="460" y2="450" stroke="white" stroke-width="4"/>
```

### Spike vs Flat Line
Represents: viral moment vs consistency, one-hit vs long game, luck vs skill
Variant of growth-curve-comparison — tighter, sharper peak that drops back to baseline.
File: `vv-style/shapes/compound/curve-spike-vs-flat.png`

```svg
<!-- Spike: flat → tight exponential rise → vertical drop back to baseline -->
<path d="M 100,540 L 300,540 C 340,540 355,470 370,410 C 378,360 385,330 390,305
  L 392,540" fill="none" stroke="white" stroke-width="1.5"/>
<!-- Flat line (right side) -->
<line x1="440" y1="540" x2="720" y2="540" stroke="white" stroke-width="1.5"/>
```

---

## Exporting as video

After generating a GSAP animation, the user may want to export it as an MP4 video.

**Always ask the user which approach they prefer:**

1. **Manual screen recording (recommended for quality)** — Use a tool like [Tella](https://tella.tv) or [Screen Studio](https://screen.studio) to record the HTML animation playing in a browser. This produces the highest-fidelity output because the browser renders glow filters, font anti-aliasing, and CSS layouts natively.

2. **Automated MP4 export (convenient, fully hands-off)** — Use the `export-mp4` skill (`skills/export-mp4/SKILL.md`). This renders frames programmatically with Python + cairosvg and stitches them with ffmpeg. No browser or manual recording needed. Minor visual differences from browser rendering (subtler glow, slightly different font weight), but the output reads well for drafts and iteration.

Read the export-mp4 skill for the full pipeline and template code.

---
<!-- Shape count: 17 shapes + 6 movement patterns (updated Batch 1) -->
<!-- Images: drop PNGs into the File paths listed above. -->
