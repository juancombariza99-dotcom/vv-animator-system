# Skill: Generate Animation

## Purpose
Take a chosen visual concept (scene flow) and produce a complete, looping GSAP HTML animation in the VV minimal style. Preview it as a widget, then save the file.

---

## Trigger phrases
- "generate the animation"
- "build the GSAP for"
- "create the HTML animation"
- "make concept [N]"
- "generate this" (after ideation)

---

## Steps

### 1. Read context files
Always read these before writing any code:

```
references/_core.md          ← shape vocabulary and SVG snippets
templates/base-gsap.html     ← the base HTML template to build from
```

If the user has a scene map from analyze-video, read that too.

### 2. Map the scene flow to SVG elements
For each scene in the concept:
- Choose the SVG element: `<circle>`, `<line>`, `<path>`, `<rect>` (with rx/ry), `<polygon>`
- Determine fill state: `fill="transparent" stroke="white"` (hollow) or `fill="white"` (solid)
- Set initial state: shapes start hidden (`opacity="0"`) or undrawn (`stroke-dashoffset` = full length)
- Position in the 405×720 canvas (x, y in SVG viewBox units = pixels)

**Canvas reference:**
- Top-left = (0, 0)
- Center = (203, 360)
- Text zone = top 25% (y < 180)
- Shape zone = middle-bottom 65% (y 180–650)
- Label zone = just below each shape

### 3. Build the GSAP timeline
Use a single `gsap.timeline({ onComplete: () => setTimeout(play, 2500) })` for looping.

**Timing conventions learned from reference videos:**
- Text fade in: 0.4–0.6s
- Ball growth from dot to ring: 0.6–0.8s, `power2.out`
- Shape draw-on (dashoffset): 0.2–0.45s per element, `power2.out`
- Ball becoming solid + glow: 0.35–0.45s, `power2.out`
- Hold on completed scene: 0.7–1.2s
- Transition fade out: 0.3s
- Ball movement between positions: 0.35–0.6s, `power2.inOut` or `power1.inOut`
- Shape morph (rx/ry): 0.5s, `power2.inOut`
- Triangle/rect scale-in from base: 0.5–0.6s, `power3.out`, `transformOrigin: '50% 100%'`

**Glow filter:** Apply when ball goes solid and lands on a shape.
```xml
<filter id="glow" x="-50%" y="-50%" width="200%" height="200%">
  <feGaussianBlur stdDeviation="6" result="blur"/>
  <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
</filter>
```
Apply: `filter: 'url(#glow)'` | Remove: `filter: 'none'`

**Draw-on pattern for paths/lines:**
Set `stroke-dasharray` = approximate path length, `stroke-dashoffset` = same value.
Animate `strokeDashoffset` to `0`. Reset in the `resetBook()` / reset function on each loop.

**Rect → oval morph:**
Use `<rect>` with `rx="0" ry="0"`. Animate `attr: { rx: 40, ry: 92 }` (adjust to half-dimensions for true oval).

### 4. Reset function
Every looping animation needs a clean reset at the top of `play()`. Set all elements back to initial state before rebuilding the timeline. Use `gsap.set()` for instantaneous resets.

### 5. Show as widget preview
After writing the code, render it using the show_widget tool so the user can see it running before the file is saved. Use the full HTML as the widget_code.

### 6. Save the file
Save to the user's workspace as `[concept-name]-gsap.html`.

---

## SVG coordinate conventions
- All positions are in the 405×720 viewBox
- Ball typically travels in the range: cy 250 (top) → 620 (bottom)
- Book baseline: y ≈ 535, spans x 80–270
- Rectangle: centered around x=203, typically 80px wide × 185px tall
- Triangle (compact): apex at y≈338, base at y≈455, width≈140px
- Text: `left: 116px; top: 192px` in CSS (absolute positioned div overlay)
- Action labels: `left: 50%; transform: translateX(-50%)` centered, below each shape

## Common mistakes to avoid
- Don't forget to reset `stroke-dashoffset` attributes (not just GSAP properties) in the reset function — use `el.setAttribute('stroke-dashoffset', ...)` directly on the DOM element.
- Don't animate SVG `fill` and `stroke` as CSS properties when using `attr` — use direct GSAP properties: `fill: 'white'`, `stroke: 'rgba(255,255,255,0)'`.
- Don't make the triangle too large — compact (140px wide) reads better than full-width.
- Ball `r` when solid on a shape: ~26px. Ball `r` when small/traveling: ~13–16px.
- Always use `power2.out` for arrivals, `power2.in` for departures.

## After generation — exporting as video

Once the animation is saved and the user is happy with it, ask if they'd like to export it as an MP4 video. If so, read the `export-mp4` skill (`skills/export-mp4/SKILL.md`) for the full pipeline. Let the user know that a manual screen recorder (Tella, Screen Studio) will give the best visual quality, but the automated export is fully hands-off if they prefer convenience.
