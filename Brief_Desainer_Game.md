# Brief & Checklist untuk Desainer Game (Visual, UI, & Level)
**Penanggung Jawab:** Muhammad Amirun Nadhif & Arya Putra Irwansyah  
**Proyek:** Chronicles of Oakhaven (Vertical Slice — 5 Fase, 1 Karakter Utama)  
**Tools:** Aseprite / LibreSprite (Pixel Art), Figma (UI & Mockup `640x360`), Godot 4 `TileMapLayer` (Susun Map)

---

## 1. Saran Pembagian Fokus (Agar Tidak Bentrok)
Agar kerja 2 desainer paralel dan cepat selesai:
* **Desainer 1:** Karakter Utama, NPC, Musuh, Potret Ekspresi Dialog, & Desain UI di Figma (`640x360`).
* **Desainer 2:** Environment Tileset `16x16` (Desa & Hutan), Ikon Item/Masakan (`16x16`), & Layout Map di Godot (`oakhaven_village.tscn` & `whispering_forest.tscn`).

---

## 2. Standar Teknis Wajib (Anti-Mixels & Anti-Rework)
1. **Resolusi Layar Game:** `640 x 360` pixel (16:9). Semua desain UI di Figma wajib memakai frame ukuran **`640 x 360`**.
2. **Grid Tileset:** Wajib **`16 x 16` pixel** per tile.
3. **Ukuran Frame Karakter:** Konsisten **`32 x 32` pixel** per frame *(atau `16 x 24` jika disepakati)*.
4. **Titik Pijak (*Anchor*):** Telapak kaki karakter/NPC **wajib menempel di bagian tengah-bawah frame** agar tidak melompat saat berganti animasi.
5. **Cukup 4 Arah:** Buat animasi **Bawah (Depan), Atas (Belakang), dan Kiri**. Arah **Kanan** tidak perlu digambar karena akan di-mirror otomatis di Godot *(kecuali karakter punya desain asimetris)*.
6. **Palet Warna:** Pilih **1 palet warna utama** (misal dari Lospec) sebelum mulai menggambar. Gunakan *tone* hangat (*Stardew*) untuk Desa Oakhaven dan *tone* biru/perak dingin (*Clair Obscur*) untuk Hutan Whispering & malam Fase 5.
7. **Format & Penamaan:** Export `.png` transparan, wajib `snake_case` tanpa spasi (prefix `spr_`, `tl_`, `ico_`, `ui_`).

---

## 3. Daftar Kebutuhan Aset (Urutan Prioritas)

### A. Tahap Awal (Agar Programmer Bisa Langsung Coding)
* [ ] 1 *Placeholder* karakter utama (`32x32`, diam & jalan 4 arah).
* [ ] 1 *Tileset* dasar sementara (rumput, tanah, air sungai, tembok/pohon batas).

### B. Karakter Utama, NPC, & Musuh
* [ ] **1 Karakter Utama Playable (`spr_hero_*`):**
  * Eksplorasi: `idle` & `walk` (Bawah, Atas, Kiri — masing-masing 2–4 frame).
  * Interaksi: animasi singkat `path_action`.
  * Combat: `combat_idle`, `attack`, `parry` *(penting untuk efek visual Reactive Parry)*, `hit`.
* [ ] **±6–8 NPC Desa (`spr_npc_*`):**
  * Cukup `idle` (2 frame) dan `walk` (2–4 frame) untuk anggota ekspedisi lain & warga kunci.
* [ ] **2 Musuh Biasa + 1 Mini-Boss (`spr_enemy_*`):**
  * Animasi: `idle`, `telegraph` *(pose ancang-ancang sebelum menyerang untuk isyarat Parry)*, `attack`, `break/hit`.
* [ ] **Potret Ekspresi Dialog (`48x48` atau `64x64`):**
  * Untuk Hero & NPC kunci: minimal ekspresi `neutral`, `sad`, `happy` (sesuai daftar dari Konseptor).

### C. Environment Tileset (`16x16`) & Ikon Item
* [ ] **Tileset Desa Oakhaven (`tl_oakhaven.png`):** Rumput, jalan tanah/batu, sungai + jembatan kayu, pagar, kebun, pohon, bangunan (Kedai *"The Golden Wheat"*, Base Camp, rumah warga), papan pengumuman, dan Tugu Peringatan.
* [ ] **Tileset Hutan Whispering (`tl_whispering_forest.png`):** Tanah lembap, pohon pinus gelap, kabut/semak, batu, gerbang keluar lembah.
* [ ] **Ikon Item (`16x16`, `ico_*`):** Herba, ikan, 3 masakan, catatan jurnal lama.

### D. Desain UI di Figma (`640x360`) & Export Aset UI (`ui_*`)
* [ ] **Kotak Dialog Naratif:** Panel gelap berbingkai kayu klasik di bagian bawah layar + kotak potret di sisi kiri.
* [ ] **Menu Kontekstual *Path Action* (`F`):** Ikon & panel mini yang muncul di atas kepala NPC.
* [ ] **HUD Eksplorasi Minimalis:** Nama lokasi, indikator Waktu (Pagi/Siang/Sore/Malam), & indikator Fase/Misi aktif di sudut layar.
* [ ] **UI Combat:** Bar HP Hero, Bar HP & **Shield/Break** Musuh, serta tombol aksi (*Attack*, *Skill*, *Item*).

---

## 4. Aturan Kerja Sama dengan Programmer & Konseptor
* **Jangan tunggu semua aset final selesai:** Serahkan aset bertahap (mulai dari versi kasar/placeholder) agar **Rahmansyah** bisa langsung memasangnya di Godot.
* **Sinkron dengan Konseptor (`Sahbilul`):** Pastikan daftar NPC, item, dan ekspresi potret yang digambar sesuai dengan tabel yang dibuat Konseptor.
* **Susun Map di Godot:** Jangan mengedit file `.tscn` yang sama secara bersamaan dengan anggota tim lain.
