# LTX-2.5 Prompt Guide: fully distilled content

Source: https://ltx.io/blog/ltx-2-5-prompt-guide (Rachel Luxemburg, 2026-08-10).
This file is the full guide content behind the summary in SKILL.md.

## Key Takeaways (official summary)

- LTX-2.5 prompts should cover: shot type, scene/lighting, action,
  character detail, camera movement, audio. Single shot = uninterrupted plan;
  dialogue-heavy scenes = screenplay style.
- Multi-shot (2–4 cuts): each cut needs explicit transition language, a
  re-established frame, and audio continuity across cuts.
- IC-LoRA tools have their own formats: Dub-It requires the full dialogue text;
  Video Editing works best with one concrete, additive instruction.

## Key Elements to Include (6 elements: official text)

1. **Establish the Shot**, Use cinematography terms that match your intended
   genre. Include shot scale or category-specific characteristics to refine the
   visual style.
2. **Set the Scene**, Describe lighting conditions, color palette, surface
   textures, and atmosphere to establish mood and tone.
3. **Describe the Action**, Write the core action as a natural sequence,
   flowing clearly from beginning to end.
4. **Define the Character(s)**, Include age, hairstyle, clothing, and
   distinguishing features. Express emotion through physical cues, not abstract
   labels.
5. **Identify Camera Movement(s)**, Specify how and when the camera moves.
   Describing how subjects appear after the movement helps the model complete
   the motion accurately.
6. **Describe the Audio**, Clearly describe ambient sound, music, speech, or
   singing. Place spoken dialogue in quotation marks. Specify language and
   accent if needed.

## Structuring Your Prompt (official principles)

- Keep the scene focused, a few clear characters and actions read better than
  a crowded frame.
- Keep lighting consistent, one coherent light logic per shot; mixed light
  sources confuse the result.
- Start simple and layer, begin with the core shot, then add detail as you
  iterate.

### Simple / Single-Shot

- One fluid paragraph; present tense verbs.
- Level of detail proportional to the shot scale (a close-up demands more detail
  than a wide shot).
- Describe camera movement relative to the subject.
- ~4–8 descriptive sentences. Iterate freely: LTX is designed for fast
  experimentation.

### Longer / Screenplay-Style

- When there is dialogue, multiple beats, or precise timing: scene headers,
  character cues, quoted dialogue. The core rules are the same.

### Length

- Not a fixed number; proportional to complexity. A simple single shot is 4–8
  sentences; screenplay scenes can be longer: every sentence must add concrete
  visual/sound detail.

## Multi-Shot Prompts (official rules)

- Write the whole scene as ONE chronological paragraph. Do NOT use a shot list,
  numbered beats, or screenplay sluglines (sluglines are only acceptable when
  you describe the cut in plain prose).

### Single-shot vs Multi-shot

| | Single-shot | Multi-shot |
|---|---|---|
| Camera | One continuous take | New framing after each cut |
| Transitions | Camera moves only (pan, push-in, etc.) | Name the edit: hard cut, match cut, dissolve, etc. |
| Continuity | Same space / subjects throughout | Re-identify subjects when they reappear; say what carries across the cut |
| Audio | One continuous soundscape | At every cut, say whether music / dialogue / ambience continues or changes |

### What to Include at Every Cut

- Name the transition in natural language: "A hard cut transitions to…", "The
  view cuts to a close-up of…", "A match cut connects…", "The image dissolves
  into…".
- Re-establish the new shot: shot scale, camera angle, who/what is in frame,
  and whether lighting changed.
- Identity consistency: use the same visual tags for recurring people/objects
  ("the woman in the red coat, earlier at the table, now…").
- State audio continuity: "the piano score continues across the cut" or
  "the dialogue drops; only wind remains."

### Tips for Strong Multi-Shot Prompts

- Prefer 2–4 shots; more than that demands short, clear beats.
- Give each shot a clear job (establish → detail → reaction; wide → medium →
  close-up).
- Keep the action chronological: "Initially…", "A moment later…",
  "Simultaneously…".
- The single-shot rules still apply: present tense, physical emotion cues,
  quoted dialogue, concrete camera language.
- If the cut does not skip time/place, avoid contradictory geography or
  unexplained costume changes.

### When to Stay Single-Shot

- When you want uninterrupted camera movement, an intimate performance, or
  lip-sync dialogue that must stay in a single frame.
- i2v (video from a first frame): prefer a single shot unless you are describing
  an intentional cut away from the opening image.

## Official Multi-Shot Example Prompt (verbatim)

> A wide shot frames a rainy city intersection at dusk, neon signs reflecting on
> wet asphalt. A young woman in a yellow raincoat walks toward camera, gripping
> a folded newspaper, while cars hiss past behind her. Soft synth music and
> distant traffic fill the air. A hard cut transitions to a medium close-up of
> her face under the hood, raindrops catching the neon as she looks off-screen
> left; the synth score continues across the cut, traffic muffled. She
> whispers, "He's late." Another hard cut jumps to a low-angle shot of a man's
> scuffed boots stepping into a puddle at the curb; the music drops to a low
> drone. He lifts his head into frame, short dark hair, soaked jacket, and
> smiles toward her off-screen as a bus rumbles past.

## Keep in Mind (model limits)

- **On-screen text**: LTX-2.5 improved short-text accuracy and fine details, but
  there is NO guarantee of consistent spelling across frames. Keep text short and
  prominent, verify it throughout the clip, and add critical titles/labels/logos
  in post.
- **Complex physics**: very chaotic motion can produce artifacts; simple,
  plausible motion is more reliable (everyday motion such as dance is fine).

## Dub-It (Speech Replacement): official section

Video-to-video: replaces the speech in an existing video. You provide the
source video + a new speech prompt.

Template: `[Speaker] is speaking [Language/Accent], saying: "[Dialogue]"`

Example: `A woman speaking in Russian saying: "Сегодня отличный день, чтобы
протестировать рабочие процессы ComfyUI для дубляжа с использованием LTX."`

- You can add emotion/delivery style to the prompt.
- Requirements: write the FULL dialogue text (the model does NOT translate);
  native script (the target language's alphabet); a single speaker (beta).
- Best practices: length ≈ the syllables/timing of the original speech;
  slightly longer > shorter. Too long = words get skipped; too short =
  slow/unnatural voice.
- Validated languages: English, French, Spanish, German, Russian.

## Video Editing IC-LoRA

- One concrete, additive instruction: what changes + what stays. (For details,
  see its own guide: the official blog "each one's guide for setup".)

## Additional Helpful Terms (full term bank: official list)

**Animation**: Stop-motion · 2D / 3D animation · Claymation · Hand-drawn
**Stylized**: Comic book · Cyberpunk · 8-bit pixel · Surreal · Minimalist ·
Painterly · Illustrated
**Cinematic**: Period drama · Film noir · Fantasy · Epic space opera · Thriller ·
Modern romance · Experimental film · Arthouse · Documentary
**Lighting**: Flickering candles · Neon glow · Natural sunlight · Dramatic shadows
**Textures**: Rough stone · Smooth metal · Worn fabric · Glossy surfaces
**Color Palette**: Vibrant · Muted · Monochromatic · High contrast
**Atmosphere**: Fog · Rain · Dust · Smoke · Particles
**Ambient Settings (sound)**: Coffeeshop noise · Wind and rain · Forest ambience
with birds
**Dialogue Style**: Energetic announcer · Resonant voice with gravitas ·
Distorted radio-style · Robotic monotone · Childlike curiosity
**Volume**: Whisper · Mutter · Shout · Scream
**Camera Language**: Follows · Tracks · Pans across · Circles around · Tilts
upward · Pushes in / pulls back · Overhead view · Handheld movement ·
Over-the-shoulder · Wide establishing shot · Static frame
**Film Characteristics**: Film grain · Lens flares · Pixelated edges · Jittery
stop-motion
**Scale Indicators**: Expansive · Epic · Intimate · Claustrophobic
**Pacing & Temporal Effects**: Slow motion · Time-lapse · Rapid cuts · Lingering
shot · Continuous shot · Freeze-frame · Fade-in / fade-out · Seamless transition ·
Sudden stop
**Visual Effects**: Particle systems · Motion blur · Depth of field
