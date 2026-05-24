# Find It — Hidden Object

> Unity · 2D/3D · mobile-first · hidden-object puzzle

---

## 1. Đây là game gì?

**Hidden object / tìm đồ trong tranh** — mỗi màn là một bức tranh (phòng ngủ, Giáng sinh, Halloween, nhà 3D…). Bạn quét cảnh, tìm vật ẩn, hoàn thành checklist và mở level tiếp theo.

---

## 2. Bạn làm gì?

| Hành động | Chi tiết |
|-----------|----------|
| **Pan / zoom** | Kéo & pinch để soi chi tiết tranh lớn |
| **Tìm vật** | Tap vào vật ẩn, hoặc **kéo thả** vào vùng đích |
| **Checklist** | Thanh UI ngang/dọc — bấm icon để gợi ý / tooltip |
| **Hoàn màn** | Hết danh sách → hiện thời gian → unlock level mới |

Flow: `Cover` → `LevelSelector` → `GameLevel/*`

---

## 3. Technical đáng chú ý

**Gameplay systems**
- `LevelManager` — dictionary target, random subset mỗi lần chơi, win detection, unlock progression
- `HiddenObj` — click vs drag (`HiddenObjFoundType`), particle/BG anim, multi-language tooltips
- `HiddenScrollView` + `HiddenObjUI` — checklist động, toggle H/V scroll
- Modular click hooks: `ClickEvent`, `MultipleClickEvent`, `SpawnSpriteOnClick`, `MusicRegion`, `DialogPanel`…
- Custom Editor (`HiddenObjEditor`, `LevelManagerEditor`) — setup level nhanh, ít code

**Mobile production**
- `CameraView2D` — pinch-zoom 2 ngón, pan clamp theo sprite bounds, re-scale khi đổi orientation/resolution
- `CameraView3D` — demo màn 3D
- Persist `GlobalSetting` → JSON (`persistentDataPath`): volume, ngôn ngữ, level đã mở
- Multi-language pipeline: text + image trackers, dialog toast

**Stack**
- Unity 6 + **URP**
- Scene mẫu: `Level1`, `CozyBedroom`, `Christmas`, `Halloween`, `3DHouse`

---

## 4. Playable / video?

| | |
|---|---|
| **WebGL (local)** | Mở `Build Web/index.html` hoặc giải nén `Build Web/Findit.zip` |
| **APK** | Thư mục `Build Apk/` (build artifact) |
| **Video** | Chưa có trong repo — *thêm link GitHub Releases / YouTube tại đây* |

```text
Find It/
├── Find It/          ← Unity project (Assets/DeskCat/FindIt)
├── Build Web/        ← WebGL playable
└── Build Apk/        ← Android build output
```
