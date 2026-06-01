# Skill: Script & Audio

## Purpose
Prepare the words and timing for an animation. Works in three modes:
- **Write** — create a script from scratch given a topic or idea
- **Refine** — adapt existing text (tweet, poem, caption, transcript) to animation style
- **Analyze** — extract rhythm and timing from an audio or video file, then align the script to those beats

Always produces a Scene Script — the shared output format that feeds into `ideate-visuals` and `generate-animation`.

---

## Trigger phrases
- "write a script for"
- "turn this into a script"
- "refine this for animation"
- "adapt this tweet / poem / caption"
- "analyze the audio / rhythm of"
- "align the script to the audio"
- "what's the timing on this"

---

## Animation style constraints
All scripts must follow these rules before passing to the next step:

| Rule | Detail |
|------|--------|
| Lowercase | all text is lowercase — no capitals except proper nouns |
| Short lines | 3–7 words per line maximum |
| One idea per line | each line = one scene beat = one thought |
| Conditional structure | favors "if / then", "when / then", "the more / the more" patterns |
| No punctuation | no periods, commas, or question marks in the displayed text |
| Present tense | "you don't have" not "you didn't have" |
| Max 4–5 lines | an animation loop is 8–15 seconds — more lines = too rushed |
| Action word at end | the final word or phrase of each scene often doubles as the action label |

---

## Mode A — Write from scratch

### When to use
User gives a concept, topic, or one-sentence idea. No existing text, no audio.

### Steps
1. Ask for the core insight in one sentence if not already given.
2. Identify the binary or conditional structure:
   - Is it a before/after? ("without X... with X...")
   - Is it a fork? ("if A... if B...")
   - Is it a sequence? ("first... then... finally...")
   - Is it a contrast? ("most people... but...")
3. Write 3–5 scene lines following the style constraints.
4. Suggest an action label for each scene (the "verb" below the shape): read, write, speak, build, ship, invest, rest, etc.
5. Output the Scene Script.

### Example
Input: "Most people spend what they earn. Wealthy people invest the difference."

Output:
```
Scene A  "most people"         → label: earn
Scene B  "spend what they earn"
Scene C  "wealthy people"      → label: invest
Scene D  "invest the difference"
```

---

## Mode B — Refine existing text

### When to use
User provides a tweet, poem, newsletter excerpt, caption, or any plain text. May be too long, too formal, or wrong structure for animation.

### Steps
1. Read the full text.
2. Extract the single core insight — what is the one thing this text is saying?
3. Identify the emotional arc: does it go from problem → solution? From confusion → clarity? From one state → another?
4. Strip to 3–5 essential beats. Cut everything that repeats or decorates without adding meaning.
5. Rewrite each beat in animation style (lowercase, short, direct).
6. Show both versions — original excerpt and refined scene lines — so the user can confirm the meaning was preserved.
7. Output the Scene Script.

### What to cut
- Filler phrases ("the truth is", "here's the thing", "look")
- Repeated ideas
- Anything that takes more than one scene to set up
- Rhetorical questions (convert to statements)
- Hashtags, emojis, handles

---

## Mode C — Analyze audio / video rhythm

### When to use
User provides an audio file (MP3, WAV) or video file (MP4) with speech or music. They want the animation timing to match the natural rhythm of the audio.

### Steps

#### 1. Extract audio (if video)
```bash
ffmpeg -i input.mp4 -vn -acodec pcm_s16le -ar 44100 audio.wav -y
```

#### 2. Detect speech pauses
Run silence detection to find where the speaker naturally pauses between phrases. These pauses become scene transition points.

```bash
ffmpeg -i audio.wav -af "silencedetect=noise=-30dB:duration=0.25" -f null - 2>&1 | grep silence
```

Output looks like:
```
silence_start: 2.84
silence_end: 3.21 | silence_duration: 0.37
silence_start: 5.19
silence_end: 5.88 | silence_duration: 0.69
```

Interpret: speech runs from 0→2.84s (Scene A), then 3.21→5.19s (Scene B), etc.
The silence duration becomes the hold time for that scene.

Adjust noise threshold if needed: `-30dB` works for clean speech. Use `-40dB` for quieter recordings.

#### Alternative: Volume analysis with pydub
For more granular timing (especially when you need to see exactly where each word lands), analyze the audio volume in small chunks:

```python
from pydub import AudioSegment

audio = AudioSegment.from_wav("voiceover.wav")
chunk_ms = 100  # 100ms resolution
for i in range(0, len(audio), chunk_ms):
    chunk = audio[i:i+chunk_ms]
    t = i / 1000.0
    try:
        db = chunk.dBFS
    except:
        db = -99
    print(f"{t:6.1f}s | {db:6.1f} dBFS")
```

This gives you a volume curve where speech shows as -15 to -30 dBFS and silence drops below -45 dBFS. You can visually identify each phrase and map it to a script line. This approach is especially useful when the silencedetect method groups multiple short phrases into one segment.

#### 3. (Optional) Transcribe with Whisper
If `openai-whisper` is available, transcribe to get word-level timestamps:
```bash
python3 -m whisper audio.wav --model small --output_format json
```
This gives exact word timing — useful for syncing text appearance to the spoken word.

If Whisper is not available, ask the user to provide the script text and map it to the detected pauses manually.

#### 4. Map script to timing
Align each script line to a speech segment:

```
Segment 0:00–2.84  → Scene A text
Segment 3.21–5.19  → Scene B text
Segment 5.88–8.40  → Scene C text
```

Hold duration for each scene = the silence that follows it (min 0.5s, round to nearest 0.1s).

---

## Output format — Scene Script

Always output in this format. This is what `generate-animation` reads.

```
## Scene Script
Source: [scratch / refined from: ... / audio: filename]
Total duration: ~Xs  |  Scenes: N  |  Loop: yes

---

Scene A  [0:00–0:00]  "text line here"
  Action label: [word]
  Hold: Xs
  Notes: [any special animation note, e.g. "ball drops onto book here"]

Scene B  [0:00–0:00]  "text line here"
  Action label: [word]
  Hold: Xs

...
```

For Mode A and B (no audio), omit timestamps and estimated Hold from the audio signal. Use default holds:
- Short line (3–4 words): 0.8s hold
- Medium line (5–6 words): 1.0s hold
- Long line (7 words): 1.2s hold

---

## Refinement loop
After outputting the Scene Script, always ask:
- "Does this capture the right meaning?"
- "Any lines to shorten, swap, or cut?"
- "Should the action labels change?"

One round of refinement before passing to `ideate-visuals` saves time on the visual concept step.
