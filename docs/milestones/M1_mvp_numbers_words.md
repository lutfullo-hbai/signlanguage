# M1 — MVP: Raqamlar + So'zlar (CPU Realtime)

**Maqsad:** ishlaydigan, realtime o'ynaydigan birinchi model. Yalang'och video
emas, **MediaPipe keypoints** asosida. Raqamlar (0-9) + bir to'plam so'zlar.
Barcha ish **CPU'da realtime** (≤50ms) ishlashi kerak.

**Nazoratchi:** ML Engineer (data partner bilan birga)

---

## Bo'limlar va Tasklar

### M1.1 — Data ishlov pipeline

#### M1.1-1. Dataset tanlash
- [ ] Raqamlar + so'zlar uchun mos dataset aniqlash.
- [ ] WLASL dan MVP'ga mos subset YOKI kichik izchil dataset.
- [ ] Har sinf uchun eng kamida ~50-100 misol.

#### M1.1-2. Yuklash skripti
- [ ] `scripts/download_*.py` — videolarni yuklash.
- [ ] URL/manifest bilan boshqarish, qayta yuklashdan himoya.

#### M1.1-3. MediaPipe Holistic
- [ ] Video → keypoints chiqarish (harframe ~126 o'lchamli vektor).
- [ ] Qo'l + tananing mag'lubiyatini (hand, face, pose) og'irlik bilan.
- [ ] `scripts/extract_keypoints.py`.

#### M1.1-4. Keypoint normalize
- [ ] Koordinata normalizatsiyasi (qo'l/kamera o'lchamiga nisbatan).
- [ ] Interpolation (frame tushib qolsa).

#### M1.1-5. Train/val/test split
- [ ] Deterministik bo'laklash (random seed).
- [ ] Sinf balansini tekshirish.

#### M1.1-6. Manifest saqlash
- [ ] `data/processed/manifests/*.csv` (path, label, split).
- [ ] Keypoint'lar `.npy` va shu partitionda saqlanadi.

### M1.2 — Model

#### M1.2-1. Model arxitektura
- [ ] `src/signlanguage/models/keypoint_model.py`
- [ ] Transformer yoki LSTM: `KeypointSequenceModel`.
- [ ] Input: (sequence_len, features), Output: sinf logits.

#### M1.2-2. Dataloader
- [ ] Sequence'larni batch qilish, padding.
- [ ] Augmentasiya (lightweight): gaussian noise, time shift.

#### M1.2-3. Train skripti
- [ ] `src/signlanguage/train.py` (config-based).
- [ ] optimizer, lr schedule, early stopping.

#### M1.2-4. Eksperiment kuzatuvi
- [ ] `mlflow` log: loss, accuracy, hp.
- [ ] Har run uchun metrikalar.

#### M1.2-5. Checkpoint saqlash
- [ ] `models/*.pt` saqlash (metric-ga asoslangan best).

### M1.3 — Real-time inference

#### M1.3-1. Live webcam skript
- [ ] `scripts/live_webcam.py` — kamera ochish, realtime o'qish.

#### M1.3-2. Sliding window
- [ ] Harakatni segmentatsiya: sign boshlanishi/tugashi aniqlash.
- [ ] Buffer (keyin padding).

#### M1.3-3. Text overlay
- [ ] OpenCV yordamida label(lar)ni ekranda ko'rsatish.

#### M1.3-4. Latency optimizasiya
- [ ] ≤50ms CPU maqsadi.
- [ ] MediaPipe faqat zarur frame'da ishlatish.

### M1.4 — Baholash (Evaluation)

#### M1.4-1. Offline eval
- [ ] Val set'da accuracy ≥60% (top-1).
- [ ] Confusion matrix (qaysi sinflar chalkash).

#### M1.4-2. Realtime test
- [ ] Videoaloqotda sinash (Zoom/Telegram kamerasi bilan).
- [ ] Foydalanuvchi tajribasi: matn paydo bo'lishi.

---

## Nazorat nuqtasi (Definition of Done)
- [ ] `scripts/live_webcam.py` realtime ishlaydi (CPU, ≤50ms)
- [ ] Model top-1 accuracy ≥60% val'da (raqamlar + so'zlar)
- [ ] Eksperiment loglari mavjud (mlflow/checkpoint)
- [ ] Kod `main`'ga merge-ready, M0 strukturasi buzilmagan

## Keyingi qadam
M2 — video-based so'z darajasiga o'tish (katta dataset) uchun sinovdan o'tgan
pipeline M1 tomonidan tayyor bo'ladi.
