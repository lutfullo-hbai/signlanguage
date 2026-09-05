# M0 — Loyiha Poydevori (Project Foundation)

**Maqsad:** professional struktura, git, environment, va asosiy kirish nuqtalari.
Bundan keyingi barcha milestone'lar shu poydevorga quriladi.

**Nazoratchi:** DevOps/MLE

---

## Tasklar

### M0-1. Git repo + struktur
- [x] Folder struktura yaratish (`src/`, `data/`, `models/`, `docs/`, `notebooks/`, `scripts/`)
- [x] `git init`, `main` branch
- [x] `.gitignore` (data modellari, venv, checkpoint — katta fayllar chiqib ketmaydi)

### M0-2. Hujjat rejasi
- [x] `README.md` — loyiha mazmuni
- [x] `docs/ROLES.md` — rollar va git metodologiya
- [x] `docs/ROADMAP.md` — umumiy reja

### M0-3. Virtual environment
- [ ] `python -m venv .venv` yaratish
- [ ] Environment'ni `source`/activate qilish
- [ ] Python 3.13 ni tasdiqlash

### M0-4. Dependency boshqaruvi
- [ ] `requirements.txt` yoki `pyproject.toml` yaratish
- [ ] Asosiy kutubxonalar: `mediapipe`, `numpy`, `opencv-python`, `torch`, `pandas`
- [ ] Qo'shimcha: `mlflow` (eksperiment log), `tqdm`

### M0-5. Bo'sh package
- [ ] `src/signlanguage/__init__.py`
- [ ] Sub-paketlar: `data/`, `models/`, `inference/`
- [ ] `python -c "import signlanguage"` ishlaydi (installed/dev mode)

### M0-6. CI (lightweight)
- [ ] pre-commit hook (line-endings, whitespace) YOKI GitHub Actions basic lint
- [ ] `ruff` yoki `flake8` config

### M0-7. Git Flow boshlash
- [ ] `develop` branch yaratish (asosiy ish joyi)
- [ ] Birinchi commit (foundation) → `develop`

---

## Nazorat nuqtasi (Definition of Done)
- [ ] `python -c "import signlanguage"` hech qanday xatosiz ishlaydi
- [ ] Barcha dependencies `pip install -r requirements.txt` bilan o'rnatiladi
- [ ] `git status` toza, `develop` branch mavjud, `main` release-ready

## Qabul mezonlari
- Environment boshqa mashinada ham qayta yaratilishi mumkin (reproducible).
- Kod strukturasi keyingi milestone'larni qo'llab-quvvatlaydi.
