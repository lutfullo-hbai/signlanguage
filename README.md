<<<<<<< HEAD
# Sign Language Translator (ASL → English)

Soqov (kar) va oddiy odamlar o'rtasidagi **realtime tarjimon**. Zoom/Telegram kabi
videovaloqotda American Sign Language (ASL) imo-ishoralarini realtime ravishda
inglizcha matnga aylantiradi.

## Maqsad & Yakuniy vazifa
Yakuniy daraja — **realtime conversation translator**:
`webcam/zoom/telegram -> MediaPipe Holistic (keypoints) -> sequence model -> English text`

Loyiha MVP'dan boshlab bosqichma-bosqich to'liq realtime conversation darajasiga
olib chiqiladi.

## Texnik yondashuv (2026 zamonaviy usul)
- To'g'ridan-to'g'ri raw video yuborish **emas**.
- **MediaPipe Holistic** yordamida tanadan qo'l/fizik **keypoints (landmarks)**
  chiqariladi (soni ~126 o'lcham/frame).
- Keypointlar **Transformer/LSTM sequence model`ga** beriladi va matn olinadi.
- Nima uchun: ~5-8ms inferens, **CPU'da realtime**, privatsiya (video serverga
  chiqmaydi, faqat geometrik koordinatalar).

## Maqsadga oid Datasetlar
| Dataset | Hajm | Maqsad |
|---|---|---|
| WLASL | 21k video / 2000 sign | Asosiy boshlang'ich |
| ASL Citizen | 83k video / 2731 sign | Kengaytirish |
| Aslense | ~108k video | Kengaytirish |
| How2Sign / OpenASL | 80h / 288h | Continuous (jumla) |

## Loyiha strukturasi
```
signlanguage/
├── docs/          # Reja, milestone, task hujjatlari
├── src/           # Python manba kodi (model, pipeline, live app)
├── data/          # raw/ va processed/ (keypoints)
├── models/        # Saqlangan checkpoints
├── notebooks/     # Exploration / ishlov berish
└── scripts/       # Yuklash, ishlov berish skriptlari
```

## Boshlanish darajasi
MVP: **raqamlar + so'zlar** (harflar A-Z ham kelajakda qo'shiladi) — realtime o'ynash.

Reja, milestone va tasklar uchun qarang: [`docs/`](docs/)
=======
# signlanguage
signlanguage american for every deaf-mute real-time translater 
>>>>>>> 3b282f7e17ebdc591597b4a5644023ba3b2e4d54
