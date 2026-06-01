# Skill: Analyze Video

## Purpose
Download a video from a URL (Instagram, YouTube) or accept an uploaded MP4/MP3, extract frames at 24fps, and produce a structured scene map that the ideate and generate skills can use as reference.

Optionally extract audio rhythm to inform animation timing.

---

## Trigger phrases
- "analyze this video"
- "look at this reel / clip"
- "download and study [URL]"
- "extract the scenes from"
- "understand the rhythm of"

---

## Steps

### 1. Get the source
- If a URL is given, download with yt-dlp:
  ```
  python3 -m yt_dlp "[URL]" -o "reel.%(ext)s"
  ```
- If an MP4/MP3 is uploaded, it's already accessible in the uploads folder.

### 2. Extract frames at 24fps
Scale to 405px wide (Instagram portrait format). Extract only the first 15 seconds unless the user specifies otherwise — that's 360 frames, enough for one loop.

```
ffmpeg -i reel.mp4 -vf "fps=24,scale=405:-1" -t 15 frames/f%04d.jpg -y
```

**Why 24fps:** At 6fps you miss in-between animation states (page turns, morphs, ball position changes). 24fps gives frame-accurate timing.

### 3. Read frames systematically
Read frames in batches. For each key moment, note:
- **What shape is visible** (circle, book, rectangle, triangle, line, etc.)
- **Fill state** (hollow outline / solid white / glow)
- **Position** in the 405×720 canvas (estimate x, y as pixel values)
- **Text content** and approximate position
- **Action labels** (read, write, speak, etc.) and their position
- **Transition type** (fade, scale, draw-on via dashoffset, morph)

Useful frame intervals to check:
- Every 12 frames (every 0.5s) for the full sequence
- Every 2-4 frames around any fast transitions

### 4. (Optional) Extract audio rhythm
If the user wants animation timing aligned to speech or music:

```
ffmpeg -i reel.mp4 -vn -acodec pcm_s16le -ar 44100 audio.wav
```

Then note: approximate beat timing, speech pauses, emphasis points. These become hold durations in the GSAP timeline.

### 5. Output a scene map
Write a structured scene map like this:

```
## Scene Map

Canvas: 405×720px  |  Duration: ~12s  |  Loops: yes

### Scene A — [condition text]
- Text: "if you don't have ideas" at top: 192px, left: 116px
- Ball: starts at cx=203, cy=250, r=1 (dot) → grows to r=26 hollow ring while falling
- Book: draws at baseline y=535, spine-first, then pages fan left+right, then baseline
- Ball lands: cx=233, cy=490, solid white + glow filter
- Label: "read" at top=556px, centered
- Hold: ~0.9s

### Transition A→B
- Ball slides LEFT cx→160 (page turn)
- Left pages fold back (dashoffset reverses lp3→lp2→lp1)
- Mid-turn arc flashes (opacity 0→1→0)
- Right pages + spine close
- Book collapses to flat line
- Ball falls: cy=555, loses glow

### Scene B — [condition text]
...
```

Save the scene map as `scene-map.md` in the working folder.

---

## Notes
- The ball is the protagonist in VV-style animations — track it in every frame.
- Solid white ball = idea formed / action happening. Hollow ring = potential / searching.
- Shapes appear below the text, centered or slightly left of center.
- Labels ("read", "write") appear below the shape, centered.
- Transitions are fast (0.1–0.4s). Holds are long (0.7–1.2s). The rhythm is: reveal → hold → transition.
