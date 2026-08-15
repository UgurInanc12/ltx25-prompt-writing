---
name: ltx25-prompt-writing
description: "Use when writing LTX-2.5 video prompts; 6-element method."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [windows, darwin, linux]
metadata:
  hermes:
    tags: [ltx-2.5, video-generation, prompt-engineering, comfyui]
    related_skills: [comfyui-desktop-windows, comfyui]
---

# LTX-2.5 Prompt Writing (from the official guide)

## When to Use

- When a prompt is needed for video generation with LTX-2.5 (ComfyUI `video_ltx2_5_t2v/flf2v/i2v`
  workflows, LTX API/Desktop/Playground).
- When the user provides a video idea → produce a "first-shot hit" production
  prompt following this skill's procedure.

Source: `https://ltx.io/blog/ltx-2-5-prompt-guide` (LTX official, 2026-08-10).
Full content + examples: `references/prompt-guide-full.md`.

## Core rules that apply to every prompt

- **Language: English** (the model is trained on English; the only exception is the
  Dub-It native-script rule).
- Present tense verbs.
- Write emotion via PHYSICAL CUES, not LABELS: not "sad" but
  "shoulders slumping, eyes downcast".
- Dialogue in quotation marks: `She whispers, "He's late."`
- Scene-focused: a few clear characters/actions beat a crowded frame.
- One light logic (mixed light sources ruin the result).
- Simple to layered: start with the core shot, then add detail through iteration.

## 6 Elements (target all of them in every prompt)

1. **Shot**: shot scale + cinematography terms (close-up, wide establishing, low-angle…).
2. **Scene**: lighting conditions, color palette, surface textures, atmosphere (mood).
3. **Action**: the core action, a natural flow from beginning to end.
4. **Character**: age, hair, clothing, distinguishing features; emotion via physical cues.
5. **Camera**: HOW and WHEN it moves; also describe how the subject looks after the
   movement (this is how the model completes the motion).
6. **Audio**: ambience, music, speech, song; dialogue in quotation marks; specify
   language/accent.

## Structure recipes

### Single-shot

- One fluid paragraph, ~4–8 sentences, present tense.
- Match the level of detail to the shot scale (a close-up needs more detail than a
  wide shot).
- Describe camera movement relative to the subject.
- In **i2v** (video from a first frame): use a single shot unless you are describing
  an intentional cut.

### Multi-shot (2–4 shots)

- One chronological paragraph; shot lists / numbered beats / sluglines are FORBIDDEN
  (a slugline is allowed when you describe the cut in plain prose).
- **At every cut**:
  - Name the transition: "A hard cut transitions to…", "A match cut connects…",
    "The image dissolves into…".
  - Re-establish the new shot: scale, angle, who/what is in frame, and whether
    lighting changed.
  - Identity consistency: recurring subjects with the same visual tag:
    "the woman in the red coat, earlier at the table, now…".
  - State audio continuity: "the piano score continues across the cut" /
    "the dialogue drops; only wind remains."
- Give shots a job: establish → detail → reaction (or wide → medium → close-up).
- Chronology: "Initially…", "A moment later…", "Simultaneously…".
- If the cut does not skip time/place, do not introduce contradictory geography or
  unexplained costume changes.
- When to stay single-shot: uninterrupted camera, intimate performance, lip-sync
  dialogue that must stay in one frame.

### Screenplay style (dialogue / multiple beats)

Scene headers + character cues + quoted dialogue; the rules are the same
(present tense, physical emotion, quoted speech). Length = complexity;
every sentence must add concrete visual/sound detail.

## Model limits (write with these in mind)

- **On-screen text**: keep it short and prominent; frame-to-frame consistency is NOT
  guaranteed; add critical titles/logos/subtitles in post.
- **Complex physics**: chaotic motion can bring artifacts; simple, plausible motion
  is reliable (everyday motion, dance included, is fine).

## Special capability formats

### Dub-It (speech replacement, video-to-video)

Template: `[Speaker] is speaking [Language/Accent], saying: "[Dialogue]"`

- Write the full dialogue text: the model does NOT translate, it follows your text.
- Native script: use the target language's alphabet (Russian → Cyrillic, Mandarin →
  Chinese characters).
- Single speaker (beta). Length ≈ the original speech (slightly longer > shorter;
  too long = words get skipped, too short = slow/unnatural voice). Validated
  languages: EN, FR, ES, DE, RU.

### Video Editing IC-LoRA

- One concrete, additive instruction: what CHANGES + what STAYS.

## Word bank (summary: full list in the reference)

- **Camera**: follows · tracks · pans across · circles around · tilts upward ·
  pushes in / pulls back · overhead view · handheld · over-the-shoulder ·
  wide establishing · static frame
- **Lighting**: flickering candles · neon glow · natural sunlight · dramatic shadows
- **Color**: vibrant · muted · monochromatic · high contrast
- **Texture**: rough stone · smooth metal · worn fabric · glossy surfaces
- **Atmosphere**: fog · rain · dust · smoke · particles
- **Style**: stop-motion · 2D/3D animation · claymation · comic book · cyberpunk ·
  8-bit pixel · film noir · period drama · documentary · arthouse…
- **Scale**: expansive · epic · intimate · claustrophobic
- **Pacing**: slow motion · time-lapse · lingering shot · freeze-frame ·
  seamless transition · sudden stop
- **Film**: film grain · lens flares · motion blur · depth of field
- **Sound**: coffeeshop noise · wind and rain · forest ambience with birds ·
  whisper / mutter / shout · distorted radio-style · robotic monotone

## Prompt building procedure (from idea → one-shot prompt)

1. Check the user's idea against the 6 elements; identify what is missing.
2. Ask about the gaps in a single message: shot scale/camera, lighting/atmosphere,
   character detail, audio, single vs multi-shot, duration.
3. Write the English prompt: one paragraph (or a chronological multi-shot paragraph),
   present tense, physical emotions, quoted dialogue, complete cut language.
4. Align with ComfyUI parameters: the `duration` widget (s), `frame_rate` (default
   24), resolution; if `prompt_enhance` is on, STILL write the full base prompt:
   enhance improves, but filling gaps is not guaranteed.
5. What raises the first-shot hit rate: simple plausible motion, one light logic,
   4–8 sentences, transition + framing + audio continuity at every cut.

## Supporting files

- `references/prompt-guide-full.md`: the fully distilled content of the official
  guide: 6-element details, multi-shot rules, example prompt, Dub-It/Video-Editing
  notes, full term bank.
