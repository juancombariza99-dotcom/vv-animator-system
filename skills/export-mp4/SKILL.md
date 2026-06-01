# Skill: Export MP4

## Purpose
Export a completed GSAP HTML animation as an MP4 video file. This is a fully automated pipeline that renders every frame programmatically using Python + cairosvg, then stitches them into an MP4 with ffmpeg. No browser or screen recorder needed.

**Important — ask the user first.** Before running this pipeline, let the user know:
- For **optimal visual quality**, a manual screen recorder like [Tella](https://tella.tv) or [Screen Studio](https://screen.studio) will produce the best results — the browser renders glow filters, anti-aliasing, and CSS text more faithfully than cairosvg.
- The **automated MP4 export** (this skill) is fully hands-off and good for quick iteration, drafts, or cases where a screen recorder isn't available. There are minor rendering differences: glow filters are subtler, and CSS-positioned text overlays must be translated to SVG `<text>` elements.

If the user chooses the automated route, proceed with the steps below.

---

## Trigger phrases
- "export as mp4"
- "export as video"
- "render to video"
- "make an mp4 of this"
- "convert animation to video"
- "save as video file"

---

## Steps

### 1. Identify the animation source

You need a completed GSAP HTML animation file (e.g., `vv-enthusiasm-gsap.html`). Read the file to understand:
- The SVG elements and their IDs
- The GSAP timeline structure (scene order, tweens, durations)
- Any CSS-positioned text overlays (`.txt`, `.action-lbl` divs)
- The total timeline duration

### 2. Choose export settings

Defaults (adjust if the user asks):
- **FPS**: 24 (smooth enough for this style; 30 for higher fidelity)
- **Resolution**: 810x1440 (2x of the 405x720 canvas for retina quality)
- **Format**: H.264 MP4 with yuv420p pixel format (universal playback)

### 3. Write the Python frame renderer

This is the core of the pipeline. You write a Python script that:

1. **Implements GSAP easing functions in Python.** The common ones used in VV animations:

```python
def power2_out(t): return 1 - (1-t)**2
def power2_in(t): return t**2
def power2_inOut(t): return 2*t*t if t < 0.5 else 1 - (-2*t+2)**2/2
def power3_out(t): return 1 - (1-t)**3
def power1_inOut(t): return 2*t*t if t < 0.5 else 1 - (-2*t+2)**2/2
def linear(t): return t

def lerp(a, b, t): return a + (b - a) * t
```

2. **Creates a `tween()` helper** for computing animation progress at any point in time:

```python
def tween(time, start, dur, ease=linear):
    if time < start: return 0.0
    if time >= start + dur: return 1.0
    return ease((time - start) / dur)
```

3. **Maps the GSAP timeline to absolute timestamps.** Walk through the GSAP timeline and compute the absolute start time of each tween. Pay attention to:
   - Relative offsets like `'-=0.3'` (overlap with previous tween)
   - `'+='` delays
   - `'<'` (start at same time as previous)
   - Absolute position values like `3.2` (seconds from timeline start)
   - Stagger values on array targets

4. **Writes a `render_frame(t)` function** that computes every element's state at time `t` and returns a complete SVG string. Key considerations:
   - CSS text overlays (`.txt` divs) must be converted to SVG `<text>` elements since cairosvg only renders SVG
   - `stroke-dashoffset` draw-on animations: compute the offset as `dash_length * (1 - progress)`
   - `scaleY` transforms on bars: compute the actual y1 coordinate as `lerp(baseline, top, progress)`
   - `opacity` is the most common animated property — use it for fades
   - The SVG must include the full `<rect>` background fill (black) since there's no HTML body
   - Include the glow filter in `<defs>` — cairosvg supports basic SVG filters

5. **Renders each frame to PNG** using cairosvg:

```python
import cairosvg

for i in range(total_frames + 1):
    t = i / FPS
    svg_str = render_frame(t)
    cairosvg.svg2png(
        bytestring=svg_str.encode('utf-8'),
        write_to=f'frames/frame_{str(i).zfill(5)}.png',
        output_width=810,
        output_height=1440
    )
```

### 4. Install dependencies

```bash
pip install cairosvg Pillow --break-system-packages -q
```

ffmpeg is pre-installed in the sandbox.

### 5. Run the renderer

Execute the Python script. At 24fps for a 16-second animation, expect ~384 frames. This typically runs within the sandbox timeout — cairosvg is fast (no browser needed).

If the animation is very long (>30s), consider:
- Reducing to 20fps
- Rendering at 1x resolution (405x720) instead of 2x
- Splitting into batches if timeout is a concern

### 6. Stitch with ffmpeg

```bash
ffmpeg -y -framerate 24 -i frames/frame_%05d.png \
  -c:v libx264 -pix_fmt yuv420p -crf 18 \
  -vf "scale=810:1440" \
  -movflags +faststart \
  output.mp4
```

Key flags:
- `-crf 18`: High quality (lower = better, 18 is visually lossless for this content)
- `-pix_fmt yuv420p`: Required for universal playback (QuickTime, web, etc.)
- `-movflags +faststart`: Puts metadata at start of file for instant playback

### 7. Verify and deliver

Check the output:
- `ffprobe output.mp4` — confirm duration, resolution, fps
- Read a few sample frames (early, middle, late) to spot-check the renders
- Save the MP4 to the user's workspace folder

---

## Known rendering differences vs browser

These are inherent to cairosvg and worth knowing:

| Feature | Browser | cairosvg |
|---------|---------|----------|
| `feGaussianBlur` glow | Bright, prominent | Subtler, tighter |
| Font rendering | System anti-aliasing | Cairo anti-aliasing (slightly different weight) |
| CSS text overlays | Rendered by browser engine | Must be converted to SVG `<text>` |
| Quadratic curves | Full browser path rendering | Faithful but minor sub-pixel differences |
| `stroke-dasharray` | Animated via GSAP | Computed manually per frame |

None of these are deal-breakers — the output reads well. But if the user needs pixel-perfect browser fidelity, recommend a screen recorder.

---

## Common mistakes to avoid

- **Don't try Puppeteer/Playwright in the sandbox.** The sandbox runs on ARM (aarch64) and Chromium binaries are x86 — browser-based capture will fail. This Python pipeline exists because of that constraint.
- **Don't forget the black background `<rect>`** in each SVG frame. Without the HTML body background, the PNG will be transparent.
- **Don't use f-strings with backslash escapes.** Python doesn't allow `\"` inside f-string expressions. Pre-compute filter attribute strings before inserting them.
- **Don't forget to convert CSS text to SVG `<text>`.** The `.txt` and `.action-lbl` divs in the HTML template are CSS-positioned — cairosvg ignores HTML entirely.
- **Match the GSAP timeline carefully.** Walk through the timeline sequentially, tracking absolute time. The relative offsets (`-=`, `+=`, `<`) compound — a small error early propagates through all later scenes.

---

## Template: easing + tween helpers

Copy this into every export script as a starting point:

```python
import os, math
import cairosvg

# ── Easing functions (match GSAP) ──
def power2_out(t): return 1 - (1-t)**2
def power2_in(t): return t**2
def power2_inOut(t): return 2*t*t if t < 0.5 else 1 - (-2*t+2)**2/2
def power3_out(t): return 1 - (1-t)**3
def power1_inOut(t): return 2*t*t if t < 0.5 else 1 - (-2*t+2)**2/2
def linear(t): return t
def back_out(t, s=1.5): return 1 + (t-1)**2 * ((s+1)*(t-1) + s)

def lerp(a, b, t): return a + (b - a) * t

def tween(time, start, dur, ease=linear):
    """Returns 0-1 progress of a tween at `time`, starting at `start` for `dur` seconds."""
    if time < start: return 0.0
    if time >= start + dur: return 1.0
    return ease((time - start) / dur)

# ── Canvas constants ──
W, H = 405, 720
FPS = 24
FRAMES_DIR = 'frames'
os.makedirs(FRAMES_DIR, exist_ok=True)

def render_frame(t):
    """Compute all element states at time t and return SVG string."""
    svg = f'''<svg viewBox="0 0 {W} {H}" xmlns="http://www.w3.org/2000/svg" width="{W*2}" height="{H*2}">
<defs>
  <filter id="glow" x="-50%" y="-50%" width="200%" height="200%">
    <feGaussianBlur stdDeviation="6" result="blur"/>
    <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
  </filter>
</defs>
<rect width="{W}" height="{H}" fill="black"/>
'''
    # ... compute element states using tween() and lerp() ...
    # ... append SVG elements ...
    svg += '</svg>'
    return svg

# ── Render loop ──
total_duration = 16.0  # adjust to match your timeline
total_frames = int(total_duration * FPS)

for i in range(total_frames + 1):
    t = i / FPS
    svg_str = render_frame(t)
    cairosvg.svg2png(
        bytestring=svg_str.encode('utf-8'),
        write_to=os.path.join(FRAMES_DIR, f'frame_{str(i).zfill(5)}.png'),
        output_width=W*2, output_height=H*2
    )
    if i % 48 == 0:
        print(f'  frame {i}/{total_frames}')

print('Done. Stitch with:')
print(f'ffmpeg -y -framerate {FPS} -i {FRAMES_DIR}/frame_%05d.png -c:v libx264 -pix_fmt yuv420p -crf 18 -movflags +faststart output.mp4')
```
