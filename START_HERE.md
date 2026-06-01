# VV Animator

A system for creating minimal, black-and-white motion graphics in the "Visualize Value" style. You provide a script (and optionally a voiceover), and your LLM walks you through storyboarding, animation, and export — step by step.

The animations use a simple visual grammar: a white ball (the protagonist), archetypal shapes (books, rectangles, triangles, lines, arrows), and short text — all on a black background. Every element earns its place. Nothing decorative.

---

## What's in this folder

```
vv-animator/
├── START_HERE.md            ← you are here
├── references/
│   ├── _core.md             ← shape vocabulary, movements, timing conventions, glow filter
│   ├── _categories.md       ← index of all reference images by type
│   └── catalog.md           ← running log of analyzed images with SVG snippets
│   └── vv-style/            ← PNG reference images organized by shape type
├── skills/
│   ├── script-audio/        ← write/refine scripts, analyze voiceover timing
│   ├── ideate-visuals/      ← propose 2-3 visual concepts from a script
│   ├── generate-animation/  ← build the GSAP HTML animation
│   ├── export-mp4/          ← render animation to MP4 video (automated)
│   └── analyze-video/       ← extract scenes from existing VV-style videos
├── templates/
│   └── base-gsap.html       ← starter HTML template for animations
└── vv-*.html                ← completed animation examples you can open in a browser
```

**Start by reading `references/_core.md`.** It contains every shape, movement, and timing convention. The skills reference it constantly.

---

## The process

### Step 1 — Understand the script
Read the full script to grasp the subject matter and emotional arc. Even though you'll only animate 10-15 seconds, the context of the whole piece matters for choosing the right visual metaphors.

If a voiceover audio file is provided, analyze it for rhythm and timing. See `skills/script-audio/SKILL.md` (Mode C) for how to detect speech segments, pauses, and map each line to a timestamp range. This timing data drives everything downstream.

If no voiceover is provided, use the default hold times from the script-audio skill (0.8-1.2s per line depending on length).

### Step 2 — Storyboard
Generate 5-8 still frames as images covering the section being animated. Each still represents a key visual moment — a "what does the screen look like right now" snapshot.

For each frame, decide:
- What text is showing
- What shape is on screen (from the vocabulary in `_core.md`)
- Where is the ball and what state is it in (hollow ring, solid, glowing)
- What labels are visible

See `skills/ideate-visuals/SKILL.md` for the full visual mapping process. Browse the PNG references in `references/vv-style/` for inspiration — they show the actual aesthetic.

Present the storyboard to the user. Refine based on feedback before moving on.

### Step 3 — Generate the animation
Once the storyboard is approved, build the GSAP HTML animation. This produces a single `.html` file that loops in any browser.

See `skills/generate-animation/SKILL.md` for the full process: SVG element setup, GSAP timeline construction, timing conventions, reset functions, and common mistakes to avoid. Use `templates/base-gsap.html` as a starting point.

If a voiceover was provided, align the GSAP timeline to the speech timestamps from Step 1. Text should appear as the speaker says the words. Shapes should draw on during natural pauses. Hold times should match the silence between phrases.

### Step 4 — Export
Once the animation looks right in the browser, export it as video.

**For best quality: use a screen recorder.** Tools like [Tella](https://tella.tv) or [Screen Studio](https://screen.studio) will capture the animation exactly as the browser renders it — glow filters, font anti-aliasing, and all. Open the HTML file in Chrome, start recording, let it play through, stop. This is the recommended approach for final output.

**For convenience: use the automated MP4 export.** See `skills/export-mp4/SKILL.md` for a fully hands-off pipeline that renders frames with Python and stitches them with ffmpeg. Minor visual differences from browser rendering (subtler glows, slightly different font weight), but good for drafts and iteration.

---

## Base prompt

Copy and paste this into Claude, ChatGPT, or any LLM that has access to this folder. Fill in the bracketed sections.

```
This is the full script:
[paste your full script here]

This is the section we will focus on:
[paste the 10-15 second section you want to animate]

[Optional — attach a voiceover audio file (.wav or .mp3) if you have one]

Use the vv-animator project and process. Inside the vv-animator project
you will find stylistic direction. You will find archetypal shapes and
effects to reference. You will also find PNGs that you can lean on to
get inspiration.

We'll only generate an animation for about 10-15 seconds. Not the
entire script. I'll tell you which part we will focus on.

Then you will:

1. Read the full script to understand the subject matter. If a voiceover
   is attached, analyze the audio for rhythm and timing.
2. Generate a storyboard of "stills" (images) for the section — about
   5-8 key frames. We can refine the storyboard at this step.
3. Once the storyboard has been approved, create the animation using
   the GSAP process outlined in the skills. Make sure the timing aligns
   with the voiceover if one was provided. Motion can be very minimal.
```

---

## Tips

- **Start small.** 10-15 seconds is one idea, 3-5 scenes. Don't try to animate the whole script at once.
- **One shape per scene.** If you're showing two shapes at the same time, the scene is probably doing too much.
- **The ball is always present.** It's the protagonist — the mind, the person, the idea. It arrives, interacts with a shape, and moves on.
- **Hold times matter more than transitions.** Let each scene breathe. The viewer needs time to read the text and absorb the shape. Fast transitions, long holds.
- **Study the examples.** Open `vv-ideas-gsap.html` or `vv-approach-gsap.html` in a browser to see completed animations. These are your north star for pacing and style.
- **Iterate the storyboard, not the code.** It's much faster to adjust still frames than to rewrite GSAP timelines. Get the storyboard right first.

---

## Reference files at a glance

| File | What it tells you |
|------|-------------------|
| `references/_core.md` | Every shape (with SVG code), movement pattern, timing convention, glow filter |
| `references/_categories.md` | Where to find reference PNGs by category |
| `references/vv-style/` | The actual PNG references — circles, rectangles, triangles, lines, compound shapes, layouts, effects |
| `templates/base-gsap.html` | The HTML/SVG/GSAP starter template |
| `vv-ideas-gsap.html` | Full working example: "if you don't have ideas / if you have ideas / but can't articulate them" |
| `vv-approach-gsap.html` | Full working example: compound effect / +1% daily / 37x difference |
