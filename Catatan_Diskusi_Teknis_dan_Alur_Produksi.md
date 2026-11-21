# Catatan Hasil Diskusi: Teknis, Desain, & Alur Produksi
**Proyek:** Chronicles of Oakhaven (Vertical Slice)  
**Penyusun / Tim:** Muhammad Amrun Nadhif & Tim  
**Tanggal:** 20 November 2026  

---

## 1. Pilihan Engine & Tools Utama
Agar proses pembuatan game 2D Pixel Art ala *Stardew Valley* + *Clair Obscur* berjalan efisien dan mudah dibantu oleh AI:

* **Game Engine:** **Godot Engine 4** (menggunakan **GDScript**)
  * *Alasan:* Engine 2D *native*, ringan, memiliki `TileMapLayer`, `Y-Sort`, dan `CanvasModulate` bawaan. Seluruh file scene (`.tscn`), resource (`.tres`), dan script (`.gd`) berbasis teks biasa sehingga sangat akurat dibaca dan diedit oleh AI.
* **Desain Aset Pixel Art (Sprite, Tileset, Ikon):** **Aseprite** *(atau **LibreSprite** / **Pixelorama** untuk alternatif gratis)*
  * *Alasan:* Ringan, khusus pixel art, mudah membuat animasi *spritesheet* untuk di-import ke Godot, dan mendukung export grid presisi.
* **Desain UI, Mockup, & Diagram GDD:** **Figma**
  * *Alasan:* Praktis untuk menyusun tata letak UI di kanvas `640x360` sebelum dipindah ke Godot, sekaligus membuat diagram *Core Gameplay Loop* untuk dokumen GDD.
* **Level / Map Editor:** **Langsung di Godot 4 (`TileMapLayer`)**
  * *Alasan:* Tidak perlu aplikasi terpisah; map bisa langsung digambar dan di-playtest di dalam Godot.
* **Version Control & Backup:** **Git / GitHub**
  * *Alasan:* Wajib digunakan untuk kolaborasi tim dan *rollback* cepat jika terjadi error saat menguji kode hasil AI.
* **Posisi AI:** Fokus sebagai **asisten produksi** (membantu coding GDScript, struktur scene Godot, dan penulisan data/dialog), bukan fitur AI runtime di dalam game, agar kontrol narasi tetap terjaga.

---

## 2. Catatan Evaluasi GDD & Penyesuaian Scope Vertical Slice
Konsep *Chronicles of Oakhaven* sudah kuat pada USP dan arah visual (`640x360` integer scaling ke `1920x1080`, tileset `16x16`). Sebelum GDD difiksasi, berikut poin yang perlu dilengkapi dan disesuaikan agar realistis untuk prototipe kuliah (45–60 menit):

### A. Bagian GDD yang Perlu Dilengkapi
* **3.1 Core Gameplay Loop (masih kosong):** Perlu diisi alur loop harian hingga ekspedisi, misalnya:
  `Pagi/Siang di Desa (Foraging, Mancing, Path Action, Naikkan Bond)` → `Sore/Malam di Base Camp (Masak bekal, atur party)` → `Ekspedisi / Combat (Reactive Parry & Break)` → `Kembali ke Desa membawa jurnal/material` → ulangi.
* **Kaitan Cozy Mechanics ↔ Combat:** Pastikan aktivitas santai (memancing, foraging, memasak, restorasi desa) berdampak langsung ke pertarungan (contoh: masakan menjadi item *heal/buff*, restorasi jembatan membuka area baru).
* **Batas Waktu Act 1:** Tentukan apakah keberangkatan ekspedisi di Chapter 1 dipicu oleh batas hari nyata (misal 7 hari) atau progres quest.

### B. Rekomendasi Pemangkasan Scope Vertical Slice (Anti *Over-Scope*)
* **Arah Gerak:** Ubah dari **8 arah** menjadi **4 arah** (Atas, Bawah, Kiri, Kanan-mirror) untuk memangkas drastis jumlah frame animasi.
* **Jumlah Karakter:** Fokuskan dulu ke **3–4 anggota Expedition 27** yang paling penting di Chapter 1 dan **5–6 NPC kunci** desa.
* **Musim:** Implementasikan **1 musim** terlebih dahulu dengan siklus waktu **Pagi–Siang–Sore–Malam**.
* **Area & Musuh:** Fokus pada **Desa Oakhaven + 1 area luar awal** dengan **1–2 jenis musuh** untuk menguji sistem *Reactive Parry* dan *Break*.

---

## 3. Alur Kerja Produksi (5 Fase Anti Kerja 2 Kali)
1. **Fase 1 — Kunci Scope & Standar Teknis:**
   Fiksasi GDD, ukuran resolusi (`640x360`), ukuran grid (`16x16` tile, ukuran karakter seragam), dan 1 palet warna (misal dari Lospec) sebelum menggambar atau ngoding.
2. **Fase 2 — Prototipe *Placeholder* di Godot 4:**
   Bangun seluruh mekanik inti menggunakan kotak warna atau aset gratis (*placeholder*) terlebih dahulu: Gerak & Y-Sort → Map kasar → Dialog & Path Action → Inventory/Masak → Combat & Reactive Parry. Jangan membuat animasi final sebelum *game feel* terasa pas.
3. **Fase 3 — Pisahkan Data Konten & Kunci UI di Figma:**
   Desain UI di Figma (`640x360`) sesuai kebutuhan sistem yang sudah berjalan. Simpan teks dialog, daftar item, resep, dan stats di file terpisah (`.json` / `.csv` / `.tres`), bukan di dalam script.
4. **Fase 4 — Produksi Aset Final & *Swap*:**
   Gambar aset final di Aseprite/LibreSprite sesuai ukuran grid Fase 1–2, lalu timpa (*replace*) file `.png` placeholder di Godot. Masukkan BGM dan SFX.
5. **Fase 5 — *Lighting*, Partikel, & Playtest:**
   Tambahkan pencahayaan siang-malam (`CanvasModulate`), partikel kelopak cahaya *The Fading*, dan lakukan *playtest* penuh Chapter 1.

---

## 4. Aturan Krusial Kerja Tim (Minim Kesalahan)
1. **Pembagian Scene & Git:**
   * Dilarang keras 2 orang mengedit file `.tscn` yang sama atau `project.godot` secara bersamaan untuk mencegah *merge conflict*.
   * Pecah game menjadi scene kecil (`player.tscn`, `npc.tscn`, `dialog_ui.tscn`, `combat.tscn`, `village_map.tscn`) dan bagi kepemilikan per anggota tim.
   * Biasakan `git pull` sebelum mulai kerja dan `git commit` per fitur kecil.
2. **Aturan Pindah File & Penamaan (`Naming Convention`):**
   * Jangan memindahkan atau me-*rename* file lewat Windows Explorer—selalu lakukan melalui panel **FileSystem Godot** agar referensi path tidak putus.
   * Gunakan huruf kecil + garis bawah (`snake_case`) tanpa spasi (contoh: `spr_aldric_walk.png`, `tl_oakhaven_grass.png`, `scn_village.tscn`).
3. **Standar Pixel Art Tim Artist:**
   * Set *Default Texture Filter* di Godot ke **`Nearest`** agar pixel art tajam dan tidak blur.
   * Jaga konsistensi ukuran piksel (*anti-mixels*) antar seluruh anggota tim.
   * Tetapkan titik pijak (*anchor*): telapak kaki karakter selalu berada di bagian tengah-bawah frame spritesheet agar animasi tidak melompat.
4. **Aturan Pakai AI dalam Tim:**
   * Kerjakan **1 fitur kecil → langsung Play/Test di Godot → Commit**, baru lanjut ke fitur berikutnya.
   * Buat 1 dokumen standar teknis (`TECH_SPEC.md`) sebagai acuan bersama agar kode yang dihasilkan AI tetap konsisten antar anggota tim.
5. **Integrasi Mingguan:**
   * Jadwalkan 1 hari setiap minggu untuk menggabungkan seluruh progres (Kode + Art + UI + Narasi) menjadi 1 *build* yang bisa dites bersama.

---

## 5. Langkah Selanjutnya (Checklist Awal)
- [ ] Diskusikan dengan tim untuk melengkapi bagian **3.1 Core Gameplay Loop** di GDD.
- [ ] Sepakati batasan final **Vertical Slice** (4 arah gerak, jumlah hero/NPC, 1 musim).
- [ ] Buat dokumen `TECH_SPEC.md` (struktur folder, aturan penamaan, ukuran sprite).
- [ ] Setup repository GitHub dan project awal Godot 4 (`640x360`, filter `Nearest`).
