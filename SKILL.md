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

# LTX-2.5 Prompt Yazma (resmi rehberden)

## When to Use

- LTX-2.5 ile video üretirken prompt yazılacaksa (ComfyUI `video_ltx2_5_t2v/flf2v/i2v`
  workflow'ları, LTX API/Desktop/Playground).
- Kullanıcı video fikri verdiğinde → bu skill'in prosedürüyle "tek atışta isabet eden"
  üretim prompt'u çıkar.

Kaynak: `https://ltx.io/blog/ltx-2-5-prompt-guide` (LTX resmi, 2026-08-10).
Tam içerik + örnekler: `references/prompt-guide-full.md`.

## Her prompt'ta geçerli temel kurallar

- **Dil: İngilizce** (model İngilizce eğitilmiştir; tek istisna Dub-It native-script kuralı).
- Present tense fiiller.
- Duyguyu ETİKETLE değil, FİZİKSEL İPUÇLARIYLA yaz — "sad" değil:
  "shoulders slumping, eyes downcast".
- Diyalog tırnak içinde: `She whispers, "He's late."`
- Sahne odaklı: birkaç net karakter/aksiyon, kalabalık kareden iyidir.
- Tek ışık mantığı (mixed light sources sonucu bozar).
- Basitten katmanlıya: önce çekirdek çekim, iterasyonla detay ekle.

## 6 Element (her prompt'ta hedefle)

1. **Shot** — çekim ölçeği + sinematografi terimleri (close-up, wide establishing, low-angle…).
2. **Scene** — ışık koşulları, renk paleti, yüzey dokuları, atmosfer (mood).
3. **Action** — çekirdek aksiyon, baştan sona doğal akış.
4. **Character** — yaş, saç, kıyafet, ayırt edici özellikler; duygu fiziksel ipuçlarıyla.
5. **Camera** — NASIL ve NE ZAMAN hareket eder; hareketten sonra öznenin nasıl
   göründüğünü de yaz (model hareketi böyle tamamlar).
6. **Audio** — ambiyans, müzik, konuşma, şarkı; diyalog tırnak içinde; dil/aksan belirt.

## Yapı reçeteleri

### Tek çekim (single-shot)

- Tek akıcı paragraf, ~4–8 cümle, present tense.
- Detay seviyesi çekim ölçeğine uysun (yakın plan geniş plandan daha çok detay ister).
- Kamera hareketini özneye göre anlat.
- **i2v**'de (ilk kareden video): kasıtlı bir kesme anlatmıyorsan tek çekim kullan.

### Çok çekim (2–4 shot)

- Tek kronolojik paragraf; shot listesi / numaralı beat / slugline YASAK
  (kesmeyi düz yazıyla anlatırsan slugline kullanılabilir).
- **Her kesmede**:
  - Geçişi adıyla söyle: "A hard cut transitions to…", "A match cut connects…",
    "The image dissolves into…".
  - Yeni çekimi yeniden kur: ölçek, açı, karede kim/ne var, ışık değiştiyse.
  - Kimlik tutarlılığı: tekrar eden özneler aynı görsel etiketle —
    "the woman in the red coat, earlier at the table, now…".
  - Ses sürekliliğini belirt: "the piano score continues across the cut" /
    "the dialogue drops; only wind remains."
- Çekimlere iş ver: establish → detail → reaction (ya da wide → medium → close-up).
- Kronoloji: "Initially…", "A moment later…", "Simultaneously…".
- Kesme zaman/yer atlamıyorsa çelişen coğrafya veya açıklanmamış kostüm değişimi yapma.
- Tek çekim ne zaman: kesintisiz kamera, samimi performans, tek karede kalması gereken
  lip-sync diyalog.

### Senaryo stili (diyalog / çoklu beat)

Scene headers + karakter ipuçları + tırnaklı diyalog; kurallar aynı
(present tense, fiziksel duygu, tırnaklı konuşma). Uzunluk = karmaşıklık;
her cümle somut görsel/ses detayı katmalı.

## Model sınırları (bunları bilerek yaz)

- **Ekran yazısı**: kısa ve belirgin tut; frame'ler arası tutarlılık garantisi YOK;
  kritik başlık/logo/subtitle'ı post'ta ekle.
- **Karmaşık fizik**: kaotik hareket artefakt getirebilir; basit, makul hareket güvenilir
  (günlük hareket — dans dahil — sorunsuz).

## Özel yetenek formatları

### Dub-It (konuşma değiştirme, video-to-video)

Template: `[Speaker] is speaking [Language/Accent], saying: "[Dialogue]"`

- Tam diyalog metnini yaz — model ÇEVİRİ YAPMAZ, senin metnini takip eder.
- Native script: hedef dilin alfabesiyle (Rusça → Kiril, Mandarin → Çince karakter).
- Tek konuşmacı (beta). Uzunluk ≈ orijinal konuşma (biraz uzun > kısa; uzun = kelime
  atlar, kısa = yavaş/doğal olmayan ses). Validated diller: EN, FR, ES, DE, RU.

### Video Editing IC-LoRA

- Tek somut, eklemeli talimat: ne DEĞİŞİYOR + ne KALIYOR.

## Kelime bankası (özet — tam liste reference'ta)

- **Kamera**: follows · tracks · pans across · circles around · tilts upward ·
  pushes in / pulls back · overhead view · handheld · over-the-shoulder ·
  wide establishing · static frame
- **Işık**: flickering candles · neon glow · natural sunlight · dramatic shadows
- **Renk**: vibrant · muted · monochromatic · high contrast
- **Doku**: rough stone · smooth metal · worn fabric · glossy surfaces
- **Atmosfer**: fog · rain · dust · smoke · particles
- **Stil**: stop-motion · 2D/3D animation · claymation · comic book · cyberpunk ·
  8-bit pixel · film noir · period drama · documentary · arthouse…
- **Ölçek**: expansive · epic · intimate · claustrophobic
- **Pacing**: slow motion · time-lapse · lingering shot · freeze-frame ·
  seamless transition · sudden stop
- **Film**: film grain · lens flares · motion blur · depth of field
- **Ses**: coffeeshop noise · wind and rain · forest ambience with birds ·
  whisper / mutter / shout · distorted radio-style · robotic monotone

## Prompt inşa prosedürü (fikirden → tek-atış prompt'a)

1. Kullanıcının fikrini 6 elemente karşı kontrol et; eksikleri belirle.
2. Eksikleri tek mesajda sor: çekim ölçeği/kamera, ışık/atmosfer, karakter detayı,
   ses, tek mi çok mu çekim, süre.
3. İngilizce prompt yaz: tek paragraf (veya çok-çekim kronolojik paragraf),
   present tense, fiziksel duygular, tırnaklı diyalog, kesme dili eksiksiz.
4. ComfyUI parametreleriyle uyumla: `duration` widget'ı (s), `frame_rate` (24 default),
   çözünürlük, `prompt_enhance` açıksa base prompt'u YİNE DE tam yaz —
   enhance iyileştirir, boşlukları doldurma garantisi yok.
5. İlk atışta tutma şansını artıranlar: basit-plausible hareket, tek ışık mantığı,
   4–8 cümle, her kesmede geçiş + çerçeve + ses sürekliliği.

## Destek dosyaları

- `references/prompt-guide-full.md` — resmi rehberin tam distillenmiş içeriği:
  6 element detayı, multi-shot kuralları, örnek prompt, Dub-It/Video-Editing notları,
  tam terim bankası.
