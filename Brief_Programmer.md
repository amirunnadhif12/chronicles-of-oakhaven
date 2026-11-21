# Brief & Checklist untuk Programmer
**Penanggung Jawab:** Rahmansyah Ragil Cahyadi  
**Proyek:** Chronicles of Oakhaven (Vertical Slice — 5 Fase, 1 Karakter Utama)  
**Engine:** Godot Engine 4 (GDScript)

---

## 1. Setup Awal & Standar Teknis
1. Jalankan langkah di `Panduan_Setup_Godot_dan_GitHub.md` untuk membuat repo GitHub (`.gitignore` Godot) dan konfigurasi awal `project.godot`:
   * Resolusi basis `640 x 360`, Stretch Mode `viewport`, Aspect `keep`, Scale Mode `integer`.
   * Default Texture Filter: **`Nearest`** (wajib agar pixel art tajam).
   * Daftarkan seluruh *Input Action* sesuai `TECH_SPEC.md` Bagian 6.
2. Buat struktur folder di panel **FileSystem Godot** sesuai `TECH_SPEC.md` (jangan memindahkan file lewat Windows Explorer).
3. Aktifkan **`Y-Sort Enabled`** pada parent node map/karakter agar posisi depan-belakang karakter terhadap pohon/bangunan otomatis rapi.

---

## 2. Arsitektur Global (`Autoload / Singletons`)
Siapkan 4 script global agar data tidak hilang saat berpindah scene (Desa ↔ Hutan ↔ Combat):
* **`GameManager.gd`:** Menyimpan `current_story_phase` (1–5), status HP/stats Hero, dan isi Inventory.
* **`QuestManager.gd`:** Melacak misi aktif dari NPC. Saat semua misi utama di fase berjalan selesai, naikkan `current_story_phase` (+1) dan kirim *signal* agar NPC/peta memperbarui kondisinya.
* **`TimeManager.gd`:** Mengatur siklus waktu (*Pagi → Siang → Sore → Malam*) dan mengatur warna `CanvasModulate`.
* **`AudioManager.gd`:** Memutar BGM, Ambience, dan SFX (terutama variasi langkah kaki dan *voice blips* dialog).

---

## 3. Urutan Pengerjaan Sistem (Gunakan *Placeholder* Dulu)
Jangan menunggu aset gambar/audio final selesai. Bangun sistem secara bertahap menggunakan kotak warna atau sprite sementara:

### Sprint 1 — Gerak, Kamera, & Peta Dasar
* [ ] `player.tscn`: Gerak 4 arah (`WASD`/Panah) + *flip* horizontal untuk arah kanan + `run` (`Shift`).
* [ ] Kamera 2D mengikuti player dengan batas (*camera limits*) sesuai ukuran map.
* [ ] Sistem transisi area (pintu/gerbang Desa Oakhaven ↔ Pinggiran Hutan Whispering, terkunci sebelum Fase 4).

### Sprint 2 — Sistem NPC, Dialog, *Path Action*, & 5 Fase Cerita
* [ ] `npc_base.tscn`: Bisa menampilkan dialog berbeda tergantung nilai `GameManager.current_story_phase`.
* [ ] `dialog_box.tscn`: Membaca data dialog dari file `.json` (folder `data/dialogs/`), menampilkan teks bertahap (*typewriter effect* + *voice blip*), dan mengganti gambar potret ekspresi (`neutral`, `sad`, `happy`).
* [ ] `path_action_menu.tscn`: Muncul di atas NPC saat menekan `F`, mengecek peluang/syarat keberhasilan, membuka info rahasia atau item, dan memengaruhi *Expedition Bond*.
* [ ] Implementasi trigger perpindahan **Fase 1 → 2 → 3 → 4 → 5** dari penyelesaian misi NPC.

### Sprint 3 — Cozy Mechanics & Inventory
* [ ] Interaksi `E` untuk mengambil herba/item (*foraging*) di titik spawn.
* [ ] Inventory sederhana + UI Jurnal/Status (`Tab` / `I`).
* [ ] Sistem Masak sederhana di Base Camp (gabungkan bahan → jadi item *heal/buff* untuk Combat).

### Sprint 4 — Combat Turn-Based + *Reactive Parry* & *Break*
* [ ] `combat_scene.tscn`: Pertarungan 1 Hero vs 1–2 Musuh.
* [ ] Giliran Hero: pilihan *Attack*, *Skill*, *Item* (dari masakan), dan *Guard*.
* [ ] **Mekanik *Reactive Parry*:** Saat giliran musuh, muncul *telegraph* (animasi + suara aba-aba) sebelum serangan mengenai hero. Jika pemain menekan `Space` tepat pada *timing window*, damage dibatalkan dan hero melakukan *Counter-Parry*.
* [ ] **Mekanik *Shield & Break*:** Setiap serangan sesuai kelemahan mengurangi poin *Shield* musuh. Jika `Shield == 0`, musuh terkena status *Break* (lewat 1 giliran + menerima damage lebih besar).

### Sprint 5 — Integrasi Aset Final, Audio, & *Polish*
* [ ] Tukar seluruh aset *placeholder* dengan `.png` final dari Desainer (`Amirun` & `Arya`).
* [ ] Pasang BGM, Ambience, dan SFX dari Sound Designer (`Arlyano`).
* [ ] Tambahkan efek pencahayaan *CanvasModulate* & partikel kelopak cahaya *The Fading*, lalu *playtest* penuh Fase 1–5.

---

## 4. Aturan Data-Driven & Kerja Sama dengan AI
1. **Pisahkan Data dari Kode:** Jangan menulis teks dialog panjang, daftar item, atau data quest langsung di dalam script `.gd`. Simpan di `.json` / `.tres` di folder `data/` agar Konseptor (**Sahbilul**) mudah mengeditnya.
2. **Aturan Pakai AI saat Ngoding:** Terapkan siklus **1 fitur kecil → jalankan Play di Godot & tes → `git commit`**, baru minta AI membuat fitur berikutnya. Selalu `git commit` sebelum merombak sistem besar.
3. **Koordinasi Scene:** Pisahkan logika UI/Combat/Player di scene masing-masing agar Desainer bisa menyusun `oakhaven_village.tscn` dan `whispering_forest.tscn` tanpa bentrok di Git.
