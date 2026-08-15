# LTX-2.5 Prompt Guide — tam distillenmiş içerik

Kaynak: https://ltx.io/blog/ltx-2-5-prompt-guide (Rachel Luxemburg, 2026-08-10).
Bu dosya, SKILL.md'deki özetin arkasındaki tam rehber içeriğidir.

## Key Takeaways (resmi özet)

- LTX-2.5 prompt'ları şunları kapsamalı: shot type, scene/lighting, action,
  character detail, camera movement, audio. Tek çekim = kesintisiz plan;
  diyalog ağırlıklı sahneler = screenplay stili.
- Multi-shot (2–4 kesme): kesme başına açık geçiş dili, yeniden kurulan çerçeve,
  kesmeler arası ses sürekliliği şart.
- IC-LoRA araçlarının kendi formatları var: Dub-It tam diyalog metni ister;
  Video Editing tek somut, eklemeli talimatla en iyi çalışır.

## Key Elements to Include (6 element — resmi metin)

1. **Establish the Shot** — Use cinematography terms that match your intended
   genre. Include shot scale or category-specific characteristics to refine the
   visual style.
2. **Set the Scene** — Describe lighting conditions, color palette, surface
   textures, and atmosphere to establish mood and tone.
3. **Describe the Action** — Write the core action as a natural sequence,
   flowing clearly from beginning to end.
4. **Define the Character(s)** — Include age, hairstyle, clothing, and
   distinguishing features. Express emotion through physical cues, not abstract
   labels.
5. **Identify Camera Movement(s)** — Specify how and when the camera moves.
   Describing how subjects appear after the movement helps the model complete
   the motion accurately.
6. **Describe the Audio** — Clearly describe ambient sound, music, speech, or
   singing. Place spoken dialogue in quotation marks. Specify language and
   accent if needed.

## Structuring Your Prompt (resmi ilkeler)

- Keep the scene focused — a few clear characters and actions read better than
  a crowded frame.
- Keep lighting consistent — one coherent light logic per shot; mixed light
  sources confuse the result.
- Start simple and layer — begin with the core shot, then add detail as you
  iterate.

### Simple / Single-Shot

- Tek akıcı paragraf; present tense fiiller.
- Detay seviyesi çekim ölçeğiyle orantılı (close-up > wide shot detay ister).
- Kamera hareketini özneye göre tanımla.
- ~4–8 betimleyici cümle. Iterate freely — LTX hızlı deneme için tasarlandı.

### Longer / Screenplay-Style

- Diyalog, çoklu beat veya hassas zamanlama varsa: scene headers, character
  cues, quoted dialogue. Temel kurallar aynı.

### Length

- Sabit sayı değil, karmaşıklıkla orantılı. Basit tek çekim 4–8 cümle;
  screenplay sahneleri daha uzun olabilir — her cümle somut görsel/ses detayı
  katmalı.

## Multi-Shot Prompts (resmi kurallar)

- Tam sahneyi TEK kronolojik paragraf olarak yaz. Shot list, numaralı beat veya
  screenplay slugline KULLANMA (kesmeyi düz yazıyla anlatmıyorsan).

### Single-shot vs Multi-shot

| | Single-shot | Multi-shot |
|---|---|---|
| Camera | One continuous take | New framing after each cut |
| Transitions | Camera moves only (pan, push-in, etc.) | Name the edit: hard cut, match cut, dissolve, etc. |
| Continuity | Same space / subjects throughout | Re-identify subjects when they reappear; say what carries across the cut |
| Audio | One continuous soundscape | At every cut, say whether music / dialogue / ambience continues or changes |

### What to Include at Every Cut

- Geçişi doğal dille adlandır: "A hard cut transitions to…", "The view cuts to a
  close-up of…", "A match cut connects…", "The image dissolves into…".
- Yeni çekimi yeniden kur: shot scale, camera angle, karede kim/ne var,
  ışık değiştiyse.
- Kimlik tutarlılığı: tekrar eden kişi/nesnelerde aynı görsel etiketleri kullan
  ("the woman in the red coat, earlier at the table, now…").
- Ses sürekliliğini belirt: "the piano score continues across the cut" veya
  "the dialogue drops; only wind remains."

### Tips for Strong Multi-Shot Prompts

- 2–4 çekim tercih et; daha fazlası kısa ve net beat'ler ister.
- Her çekime net bir iş ver (establish → detail → reaction; wide → medium → close-up).
- Aksiyonu kronolojik tut: "Initially…", "A moment later…", "Simultaneously…".
- Single-shot kuralları aynen geçerli: present tense, fiziksel duygu ipuçları,
  tırnaklı diyalog, somut kamera dili.
- Kesme zaman/yer atlamıyorsa çelişen coğrafya veya açıklanmamış kostüm
  değişiminden kaçın.

### When to Stay Single-Shot

- Kesintisiz kamera hareketi, samimi performans veya tek karede kalması gereken
  lip-sync diyalog istiyorsan.
- i2v (ilk kareden video): açılış görüntüsünden kasıtlı kesme anlatmıyorsan
  tek çekim tercih et.

## Resmi Multi-Shot Örnek Prompt (birebir)

> A wide shot frames a rainy city intersection at dusk, neon signs reflecting on
> wet asphalt. A young woman in a yellow raincoat walks toward camera, gripping
> a folded newspaper, while cars hiss past behind her. Soft synth music and
> distant traffic fill the air. A hard cut transitions to a medium close-up of
> her face under the hood, raindrops catching the neon as she looks off-screen
> left; the synth score continues across the cut, traffic muffled. She
> whispers, "He's late." Another hard cut jumps to a low-angle shot of a man's
> scuffed boots stepping into a puddle at the curb; the music drops to a low
> drone. He lifts his head into frame — short dark hair, soaked jacket — and
> smiles toward her off-screen as a bus rumbles past.

## Keep in Mind (model sınırları)

- **On-screen text**: LTX-2.5 kısa metin doğruluğunu ve ince detayları
  iyileştirdi ama frame'ler arası tutarlı yazım garantisi YOK. Metni kısa ve
  belirgin tut, klip boyunca doğrula, kritik başlık/etiket/logo'yu post'ta ekle.
- **Complex physics**: çok kaotik hareket artefakt üretebilir; basit, makul
  hareket daha güvenilir (dans gibi günlük hareket sorunsuz).

## Dub-It (Speech Replacement) — resmi bölüm

Video-to-video: mevcut videodaki konuşmayı değiştirir. Kaynak video + yeni
konuşma prompt'u verilir.

Template: `[Speaker] is speaking [Language/Accent], saying: "[Dialogue]"`

Örnek: `A woman speaking in Russian saying: "Сегодня отличный день, чтобы
протестировать рабочие процессы ComfyUI для дубляжа с использованием LTX."`

- Prompt'a duygu/teslimat stili eklenebilir.
- Requirements: TAM diyalog metni yaz (model çeviri YAPMAZ); native script
  (hedef dil alfabesi); tek konuşmacı (beta).
- Best practices: uzunluk ≈ orijinal konuşmanın hece/timing'i; biraz uzun > kısa.
  Çok uzun = kelime atlanır; çok kısa = yavaş/doğal olmayan ses.
- Validated diller: English, French, Spanish, German, Russian.

## Video Editing IC-LoRA

- Tek somut, eklemeli talimat: ne değişiyor + ne kalıyor. (Detaylar için kendi
  rehberi: resmi blog "each one's guide for setup".)

## Additional Helpful Terms (tam terim bankası — resmi liste)

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
