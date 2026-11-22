# ريل أنيميشن عنك إنت: شخصية 3D من صورك + فيديو على RunPod

**دليل خطوة بخطوة، بالعربي والإنكليزي · Step-by-step guide, Arabic and English**

From the GTA 6 night reel by [@alihaidar.dev](https://www.instagram.com/alihaidar.dev/). Written from the setup
used to make it on 2026-11-21/22. Prices change; check them on runpod.io before you start.

---

## بالعربي

### شو بتحتاج

| شو | ليش | السعر |
| --- | --- | --- |
| **ChatGPT** (GPT Image 2) | يحوّل صورتك لشخصية أنيميشن 3D، ويرسم كل لقطة | ضمن اشتراك ChatGPT |
| **حساب RunPod** | كرت شاشة قوي بالساعة | تقريباً $1–3 بالساعة حسب الكرت |
| **[Freefield](https://github.com/neuregex/freefield)** | نسخة open source من تطبيقات Higgsfield على ComfyUI، ببلاش | $0 |
| **صوتك إنت** | مسجّل عالتلفون | $0 |
| CapCut أو أي برنامج مونتاج | تجميع اللقطات والترجمة | $0 |

⚠️ **وقّف الـpod لما تخلّص.** بيحسب عليك عالساعة حتى لو ما عم يعمل شي.

### 1. الشخصية (أهم خطوة)

1. اختار صورة واضحة لوجهك من قدّام، ضو منيح، بلا نضارات شمس.
2. اختار **صورة style**: فريم من فيلم أو ريل أنيميشن عاجبك ستايله.
3. ارفع الصورتين على ChatGPT وحط هالـprompt (غيّر الوصف ليصير عنك):

```
Turn me (photo 1) into a Pixar movie character, in exactly the animated style of image 2:
fully stylised 3D cartoon, Pixar/Disney human design with exaggerated appealing proportions,
big expressive cartoon eyes, simplified smooth features, sculpted stylised hair and beard.
Style comes first; it must look like a frame from an animated movie, never a photo.
Keep my [hair / beard / brows] so friends would recognise me. [Clothes].
[The scene: where you are, the time, the light]. No text. Portrait 2:3.
```

**الدرس اللي تعلّمناه:** إذا شدّدت كتير على "خليه يشبهني"، بيطلع الوجه حقيقي مع عيون كرتون وبيخوّف.
خلّي **الستايل أول**، والشبه بتفاصيل قليلة (الشعر، الدقن، الحواجب).

4. بس تعجبك الشخصية، كل لقطة جديدة: ارفع **صورة الشخصية** + اوصف اللقطة. وزيد دايماً:
   - `Both eyes look at the same point, pupils aligned.` (وإلا العيون بتطلع مش مركّزة)
   - `Both hands fully visible and natural.` (الإيدين أكتر شي بيخرب)

### 2. شغّل Freefield على RunPod (كبسة وحدة)

1. اعمل حساب على runpod.io وحط $10–25 رصيد.
2. **حساب Hugging Face ببلاش** ← Settings ← Access Tokens ← اعمل token نوعه Read.
   وبـ RunPod: Settings ← Secrets ← اعمل secret اسمو `hf_token` وحط الـtoken فيه.
3. افتح **[template تبع Freefield على RunPod](https://console.runpod.io/deploy?template=p7g587ry3j)**.
4. **الكرت:** للتطبيقات العادية 24 GB بيكفّوا. لـ **MiniMax H3** (أحسن موديل فيديو open weight هلّق،
   هو اللي حرّك لقطات الريل) بدك كرت كبير: نحنا استعملنا RTX PRO 6000 (96 GB) بـ $2.69 بالساعة.
   حسب Freefield، L40S (48 GB) بيشغّل كل التطبيقات.
5. **Add volume ← Volume disk**، 60 GB على `/workspace`. (صفحة الـdeploy ما بتزيدها لحالها.)
6. Deploy، وبعدين افتح **Logs**: بيطلعلك رابط الـstudio مع passcode.
   ما تشارك الرابط مع حدا: أي حدا معو ياه بيستعمل الكرت تبعك.

### 3. حرّك اللقطات

بالـstudio، لكل لقطة:

- **H3 Photo** (`h3-photo`): ارفع الصورة واوصف الحركة. مثال من الريل:
  *"He types on the laptop, the phone on the desk buzzes and lights up, he stops typing and his eyes glance
  down at the phone, then he reaches for it. Slow gentle camera push-in. 3D animated feature-film shot,
  smooth natural motion, consistent character, no speech."*
  كل لقطة 3–5 ثواني، أخدت 1–2.5 دقيقة على الـPRO 6000.
- **Talking** (`talking`): للّقطات اللي بتحكي فيها. ارفع صورة الشخصية + **تسجيل صوتك**، وبتتحرّك
  الشفاف عالكلام. ⚠️ بيطلّع فيديو عريض 16:9: حط الصورة بنص خلفية عريضة، وبعدين قصّ الـ9:16 من النص.
- **Upscale Video** (`upscale-video`): يكبّر كل لقطة لـ1080p.
- **SFX** (`sfx`): موسيقى بيانو هادية، صوت كيبورد، رجّة تلفون.

### 4. نصايح من التجربة

- **الشاشات والنصوص ما تخلّي الـAI يرسمها.** بيطلع الكلام مخربط. شاشة الواتساب بالريل عملناها HTML
  حقيقي وركّبناها فوق التلفون بالمونتاج.
- **صوتك الحقيقي** أحسن من أي صوت AI. سجّل كل جملة مرتين بغرفة هادية.
- إذا لقطة خربت (إيدين، لابتوب بمكان غريب)، ارجع لـChatGPT وصلّح الصورة **قبل** ما تحرّكها.
- **رخصة MiniMax H3:** الرخصة بتستثني الاتحاد الأوروبي، بريطانيا، كوريا الجنوبية وأميركا. إذا إنت هونيك،
  اقرأها أو استعمل LTX-2.5 (تطبيقات `video`) بدالها.

### 5. التجميع

بـ CapCut: رتّب اللقطات، حط صوتك، الموسيقى تحت الصوت، وترجمة عربي + إنكليزي.
وبعدين **Terminate** للـpod (template تبع Freefield ما بيحفظ شي بعد ما توقّفه، إلا إذا عملت network volume).

---

## English

### What you need

| Item | Why | Cost |
| --- | --- | --- |
| **ChatGPT** (GPT Image 2) | Turns your photo into a 3D animated character and draws every shot | Your ChatGPT plan |
| **RunPod account** | A strong GPU by the hour | About $1–3/hour depending on the GPU |
| **[Freefield](https://github.com/neuregex/freefield)** | Open-source rebuild of Higgsfield's apps on ComfyUI, open weights | Free (MIT) |
| **Your own voice** | Recorded on your phone | Free |
| CapCut or any editor | Assembly and captions | Free |

⚠️ **Stop the pod when you're done.** An idle pod bills the same as a busy one.

### 1. The character (the step that matters most)

1. Pick a clear, front-facing, well-lit photo of yourself. No sunglasses.
2. Pick a **style frame**: a still from an animated film or reel whose look you want.
3. Upload both to ChatGPT with this prompt (fill in your own details):

```
Turn me (photo 1) into a Pixar movie character, in exactly the animated style of image 2:
fully stylised 3D cartoon, Pixar/Disney human design with exaggerated appealing proportions,
big expressive cartoon eyes, simplified smooth features, sculpted stylised hair and beard.
Style comes first; it must look like a frame from an animated movie, never a photo.
Keep my [hair / beard / brows] so friends would recognise me. [Clothes].
[The scene: where you are, the time, the light]. No text. Portrait 2:3.
```

**Lesson learned:** push likeness too hard and you get a real face with cartoon eyes, which looks
uncanny. Put **style first** and keep likeness to a few features (hair, beard, brows).

4. Once you like the character, make each shot from **the character image** plus a description of the shot.
   Always add:
   - `Both eyes look at the same point, pupils aligned.` (otherwise the eyes drift)
   - `Both hands fully visible and natural.` (hands break most often)

### 2. Run Freefield on RunPod (one click)

1. Sign up at runpod.io and add $10–25 of credit.
2. Make a **free Hugging Face account** → Settings → Access Tokens → a Read token. In RunPod:
   Settings → Secrets → a secret named `hf_token` holding that token.
3. Open **[Freefield's RunPod template](https://console.runpod.io/deploy?template=p7g587ry3j)**.
4. **GPU:** 24 GB runs most apps. **MiniMax H3** (currently the best open-weight video model, and the
   one that animated this reel) needs a big card: we used an RTX PRO 6000 (96 GB) at $2.69/hour.
   Freefield says an L40S (48 GB) runs every app.
5. **Add volume → Volume disk**, 60 GB at `/workspace`. The deploy page doesn't add it by itself.
6. Deploy, then open **Logs**: you'll get the studio link and a passcode. Don't share the link;
   anyone with it can use your GPU.

### 3. Animate the shots

In the studio, for each shot:

- **H3 Photo** (`h3-photo`): upload the still and describe the motion. From the reel:
  *"He types on the laptop, the phone on the desk buzzes and lights up, he stops typing and his eyes glance
  down at the phone, then he reaches for it. Slow gentle camera push-in. 3D animated feature-film shot,
  smooth natural motion, consistent character, no speech."*
  Each 3–5 s shot took 1–2.5 minutes on the PRO 6000.
- **Talking** (`talking`): for the lines you speak. Upload the character image and **your recorded line**;
  the lips move to it. ⚠️ It outputs a wide 16:9 frame: put your portrait in the middle of a wide
  background, then crop the 9:16 out of the centre.
- **Upscale Video** (`upscale-video`): brings every clip to 1080p.
- **SFX** (`sfx`): soft piano, keyboard taps, phone buzz.

### 4. Tips from doing it

- **Don't let AI draw screens or text.** It comes out garbled. The WhatsApp chat in the reel is real HTML,
  composited onto the phone in the edit.
- **Your real voice** beats any AI voice. Record each line twice in a quiet room.
- If a shot breaks (hands, a laptop at a strange angle), fix the still in ChatGPT **before** animating it.
- **MiniMax H3 licence:** it excludes the EU, the UK, South Korea and the US. If you're there, read it, or
  use LTX-2.5 (the `video` apps) instead.

### 5. Assemble

In CapCut: order the clips, lay your voice on top, music under the voice, captions in your languages.
Then **Terminate** the pod (Freefield's template keeps nothing after that unless you set up a network volume).

### Links

- Freefield: https://github.com/neuregex/freefield (its [cloud GPU guide](https://github.com/neuregex/freefield/blob/main/docs/cloud-gpus.md) covers volumes that outlive the pod)
- MiniMax H3, LTX-2.5 and every other model, with licences: listed per app in Freefield's `apps/*/app.json`
- RunPod pricing: https://www.runpod.io/pricing
- Cheaper b-roll only (Wan 2.2 + LTX-2.5): [wan-setup](https://github.com/alihaidar2950/wan-setup)

---

### What next? · شو بعد؟

- ⭐ Star this repo if it helped, so more people find it.
- Follow [@alihaidar.dev](https://www.instagram.com/alihaidar.dev/) on Instagram or [TikTok](https://www.tiktok.com/@alihaidar.dev) for the next free guide.
- All my free guides: [github.com/alihaidar2950](https://github.com/alihaidar2950?tab=repositories)

<div dir="rtl">

إذا فادك، حطّ ⭐ عالـrepo، وتابعني عَ [إنستغرام](https://www.instagram.com/alihaidar.dev/) أو [تيك توك](https://www.tiktok.com/@alihaidar.dev) لتوصلك الأداة الجاية ببلاش.

</div>
