# ROADMAP — ASL → English Realtime Translator

## Umumiy yo'nalish (Trajectory)
Bosqichma-bosqich MVP → to'liq **realtime conversation translator**.

```
M0: Loyiha poydevori
  ↓
M1: MVP — raqamlar + so'zlar (CPU realtime)
  ↓
M2: Video-based so'z darajasi (katta dataset, ~1000-2000 sign)
  ↓
M3: Fingerspelling (A-Z) qo'shish
  ↓
M4: Continuous / sentence (LSTM/Transformer seq2seq)
  ↓
M5: Realtime conversation translator (Zoom/Telegram integrasiya)
```

Har bir milestone: `docs/milestones/M<n>_<nama>.md` faylida batafsil tasvirlanadi,
tasklar bilan. Shuningdek checklist `docs/checklists/` da.

---

# MVP Rejasi (M0 + M1)

## M0 — Loyiha Poydevori (Project Foundation)
**Maqsad:** professional struktura, git, environment, va asosiy kirish nuqtalari.

| # | Task | Tavsif | Rol | Status |
|---|------|--------|-----|--------|
| M0-1 | Git repo + struktur | Folderlar, `.gitignore`, `main` branch | DevOps | ✅ |
| M0-2 | Hujjat rejasi | README, ROLES, ROADMAP | Docs | ✅ |
| M0-3 | Virtual environment | `venv`, Python 3.13 | DevOps | ⬜ |
| M0-4 | Dependency boshqaruvi | `pyproject.toml` / `requirements.txt` | DevOps | ⬜ |
| M0-5 | Bo'sh package | `src/signlanguage/` bo'sh package + `__init__` | ML | ⬜ |
| M0-6 | CI (lightweight) | Lint + import check (pre-commit yoki GH Actions) | DevOps | ⬜ |
| M0-7 | Git Flow boshlash | `develop` branch yaratish | DevOps | ⬜ |

**Nazorat nuqtasi (M0 done):**
- [ ] `python -c "import signlanguage"` ishlaydi
- [ ] `git status` toza, `develop` branch mavjud

---

## M1 — MVP: Raqamlar + So'zlar (Static-ish + basic motion, CPU realtime)

**Maqsad:** ishlaydigan, realtime o'ynaydigan birinchi model. Yalang'och video emas,
**MediaPipe keypoints** asosida. Raqamlar (0-9) + bir to'plam so'zlar (salom, rahmat,
ha, yo'q, ...).

### M1.1 — Data ishlov pipeline
| # | Task | Tavsif | Rol |
|---|------|--------|-----|
| M1.1-1 | Dataset tanlash | MVP'ga mos dataset: raqamlar + so'zlar (WLASL subset / Mahjong kabi kichik) | Data |
| M1.1-2 | Yuklash skripti | `scripts/download_*.py` — videolarni yuklash | Data |
| M1.1-3 | MediaPipe Holistic | Video → keypoints chiqarish (video→116-126 vec/frame) | Data |
| M1.1-4 | Keypoint normalize | Koordinata normalizatsiya (qo'l o'lcham/joyiga nisbatan) | Data |
| M1.1-5 | Train/val/test split | Deterministik bo'lish, balans | Data |
| M1.1-6 | Manifest saqlash | `data/processed/manifests/*.csv` | Data |

### M1.2 — Model
| # | Task | Tavsif | Rol |
|---|------|--------|-----|
| M1.2-1 | Model arxitektura | Transformer və ya LSTM: `KeypointSequenceModel` | ML |
| M1.2-2 | Dataloader | Sequence'larni batch qilish | ML |
| M1.2-3 | Train skripti | `src/.../train.py` (config-based) | ML |
| M1.2-4 | Eksperiment kuzatuvi | MLflow yoki wandb logging | ML |
| M1.2-5 | Checkpoint saqlash | `models/` ga `.pt` saqlash | ML |

### M1.3 — Real-time inference
| # | Task | Tavsif | Rol |
|---|------|--------|-----|
| M1.3-1 | Live webcam skript | `scripts/live_webcam.py` — realtime o'qish | ML/Backend |
| M1.3-2 | Sliding window | Harakatni segmentatsiya qilish (sign aniqlash) | ML |
| M1.3-3 | Text (labellarni) ekranda ko'rsatish | OpenCV overlay | Backend |
| M1.3-4 | Latency optimizasiya | ≤50ms CPU maqsadi | MLE |

### M1.4 — Baholash (Evaluation)
| # | Task | Tavsif | Rol |
|---|------|--------|-----|
| M1.4-1 | Offline eval | Val set'da accuracy (≥60% top-1) | ML |
| M1.4-2 | Realtime test | Videoaloqotda sinash (kamera) | All |

**Nazorat nuqtasi (M1 done):**
- [ ] `scripts/live_webcam.py` realtime ishlaydi (CPU, ≤50ms)
- [ ] Model top-1 accuracy ≥60% val'da (raqamlar+so'zlar)
- [ ] Zoom/Telegram GPU'da ham ishlashga tayer (code kiritilgan)

---

# Keyingi Milestone'lar (qisqacha tasviri)

## M2 — Video-based So'z Darajasi
- WLASL/ASL Citizen katta videolardan keypoint chiqarish.
- Vocabulary ~1000-2000 eng keng tarqalgan sign.
- Modelni kengaytirish, accuracy'ni oshirish.

## M3 — Fingerspelling (A-Z)
- Alifbo harflari uchun keypoint + classification qo'shish.
- Ism/joy yozish uchun.

## M4 — Continuous / Sentence
- LSTM/Transformer seq2seq (video → jumla).
- Gloss-free yondashuv, How2Sign/OpenASL.

## M5 — Realtime Conversation Translator
- Zoom/Telegram videovaloqotga integratsiya (OBS virtual camera, overlays).
- On-screen realtime subtitle tizimi.
- 1.0.0 release.
