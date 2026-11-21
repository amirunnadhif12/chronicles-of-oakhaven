# TECH_SPEC.md — Standar Teknis Tim Chronicles of Oakhaven
*Dokumen ini menjadi acuan tunggal untuk seluruh anggota tim (Programmer, Artist, UI, Penulis) dan AI Assistant agar hasil kerja seragam dan tidak bentrok.*

---

## 1. Spesifikasi Engine & Display (Godot 4)
* **Engine:** Godot Engine 4.x (GDScript)
* **Resolusi Basis (Viewport):** `640 x 360` (rasio 16:9)
* **Target Window / Fullscreen:** `1920 x 1080` (Integer Scaling 3x)
* **Stretch Mode:** `viewport` | **Aspect:** `keep` | **Scale Mode:** `integer`
* **Default Texture Filter:** `Nearest` *(Wajib agar pixel art tajam, tidak blur)*

---

## 2. Struktur Folder Project Godot
Dilarang memindahkan atau me-*rename* file lewat Windows Explorer. Selalu lakukan dari panel **FileSystem** di dalam Godot.

```text
res://
├── assets/
│   ├── sprites/
│   │   ├── characters/     # Spritesheet hero & NPC
│   │   ├── enemies/        # Spritesheet musuh
│   │   ├── tilesets/       # Tileset 16x16 (desa, hutan, interior)
│   │   ├── items/          # Ikon herba, ikan, masakan (16x16)
│   │   └── ui/             # Frame dialog, potret, ikon Path Action
│   ├── audio/
│   │   ├── bgm/            # Musik latar (.ogg / .mp3)
│   │   └── sfx/            # Efek suara (.wav)
│   └── fonts/              # Font pixel art (.ttf / .otf)
├── data/                   # File data konten (.json / .tres)
│   ├── dialogs/
│   ├── items/
│   └── quests/
├── scenes/
│   ├── actors/             # player.tscn, npc_base.tscn, enemy_base.tscn
│   ├── maps/               # oakhaven_village.tscn, whispering_forest.tscn
│   ├── combat/             # combat_scene.tscn, combat_unit.tscn
│   ├── ui/                 # hud.tscn, dialog_box.tscn, path_action_menu.tscn
│   └── main.tscn           # Scene utama pengelola transisi
└── scripts/
    ├── autoload/           # Global scripts (GameManager, TimeManager, AudioManager)
    ├── actors/
    ├── combat/
    └── ui/
```

---

## 3. Aturan Penamaan (`Naming Convention`)
Seluruh nama file, folder, dan variabel di Godot wajib memakai **`snake_case` (huruf kecil + garis bawah, tanpa spasi, bahasa Inggris)**:

| Jenis File | Prefix | Contoh Benar | Contoh Salah |
| :--- | :--- | :--- | :--- |
| Spritesheet / Gambar | `spr_` | `spr_aldric_walk.png` | `Aldric Walk.png` |
| Tileset | `tl_` | `tl_oakhaven_ground.png` | `Tileset Desa.png` |
| Ikon Item / UI | `ico_` / `ui_` | `ico_herb_moonleaf.png`, `ui_dialog_frame.png` | `icon1.png` |
| Scene (`.tscn`) | *(deskriptif)* | `player.tscn`, `oakhaven_village.tscn` | `SceneBaru.tscn` |
| Script (`.gd`) | *(sesuai scene)* | `player.gd`, `dialog_box.gd` | `PlayerScript.gd` |
| Audio BGM / SFX | `bgm_` / `sfx_` | `bgm_oakhaven_day.ogg`, `sfx_parry_hit.wav` | `lagu desa.mp3` |

---

## 4. Standar Pixel Art untuk Tim Artist
* **Grid Tileset:** `16 x 16` pixel per tile.
* **Ukuran Frame Karakter (Eksplorasi):** Disarankan konsisten **`32 x 32` pixel per frame** (atau `16 x 24` — *pilih satu sebelum mulai*).
* **Titik Pijak (*Anchor*):** Telapak kaki karakter **wajib berada di tengah-bawah frame** agar posisi karakter tidak melompat/geser saat berganti animasi (`idle` ↔ `walk`).
* **Format Export:** `.png` transparan (tanpa *compression blur*), disusun rapi dalam *spritesheet* horizontal per animasi atau satu *grid* seragam.
* **Anti-Mixels:** Semua aset harus digambar pada skala piksel yang sama (jangan memperbesar gambar `16x16` menjadi `32x32` secara manual jika detailnya jadi belang).

---

## 5. Susunan Tim, Pembagian Kerja, & Aturan Git
### Susunan Role Tim
* **Desainer Game (Visual, UI, & Level):** Muhammad Amirun Nadhif & Arya Putra Irwansyah
* **Programmer:** Rahmansyah Ragil Cahyadi
* **Sound Designer:** Moh. Arlyano Swandaru
* **Konseptor (Narasi, Fase, & Dialog):** Muhammad Sahbilul Khoir

### Aturan Git & Kolaborasi (Anti-Konflik)
1. **Dilarang mengedit file `.tscn` yang sama atau `project.godot` secara bersamaan.**
   * *Programmer* (`Rahmansyah`) memegang logika script (`.gd`), sistem combat, `QuestManager`, dan `dialog_box.tscn`.
   * *Desainer Game* (`Amirun` & `Arya`) menyiapkan aset `.png` (`assets/sprites/`), layout UI di Figma, serta menyusun map di `oakhaven_village.tscn` / `whispering_forest.tscn` (satu map satu penanggung jawab).
2. **Alur Git Harian:**
   * `git pull` sebelum mulai kerja.
   * Kerjakan 1 fitur/aset kecil → **Play & Test di Godot** → `git commit -m "feat: deskripsi singkat"` → `git push`.
   * Selalu `git commit` sebelum meminta AI merombak kode besar.

---

## 6. Input Map Standar (Sesuai GDD 3.5)
Nama *Input Action* di *Project Settings → Input Map* Godot:
* `move_up` (`W` / Panah Atas)
* `move_down` (`S` / Panah Bawah)
* `move_left` (`A` / Panah Kiri)
* `move_right` (`D` / Panah Kanan)
* `interact` (`E` / `Enter`)
* `action_parry_run` (`Space` / `Shift Kiri`)
* `path_action` (`F`)
* `menu_journal` (`Tab` / `I`)
* *(Opsional)* `quick_slot_prev` (`Q`) & `quick_slot_next` (`R`) — menggantikan fungsi ganti pemimpin karena game fokus ke **1 karakter utama**
