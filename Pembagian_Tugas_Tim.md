# Pembagian Tugas & Dokumen Acuan Tim — Chronicles of Oakhaven

| Nama Anggota | Role | Fokus Tugas Utama (Vertical Slice) | Dokumen Acuan |
| :--- | :--- | :--- | :--- |
| **Muhammad Amirun Nadhif** & **Arya Putra Irwansyah** | Desainer Game *(Visual, UI, & Level)* | Desain pixel art (`16x16` tileset, `32x32` 1 hero & NPC, potret), layout UI `640x360` di Figma, desain map Desa Oakhaven & Hutan Whispering, serta finalisasi GDD. | `Brief_Desainer_Game.md`, `TECH_SPEC.md`, `Draft_GDD_3_1_dan_Vertical_Slice.md` |
| **Rahmansyah Ragil Cahyadi** | Programmer | Setup repo GitHub & Godot 4 (`640x360`, `Nearest`), membangun sistem inti (gerak 4 arah, dialog & *Path Action*, sistem 5 Fase misi NPC, *Cozy mechanics*, & *Combat Reactive Parry*). | `Brief_Programmer.md`, `Panduan_Setup_Godot_dan_GitHub.md`, `TECH_SPEC.md` |
| **Moh. Arlyano Swandaru** | Sound Designer | Membuat/menyiapkan 5 BGM (`.ogg`, *seamless loop*), 2 Ambience, dan daftar SFX (`.wav`, potong jeda awal) termasuk *voice blips* dan *telegraph/parry* combat. | `Brief_Sound_Design.md`, `TECH_SPEC.md` |
| **Muhammad Sahbilul Khoir** | Konseptor | Menetapkan 1 karakter utama & 5 anggota lain sebagai NPC, profil ±6–8 NPC, rincian misi **Fase 1–5**, naskah dialog tabel (maks 2–3 baris/kotak), serta daftar item & jurnal lama. | `Brief_Konseptor_Narasi.md`, `Draft_GDD_3_1_dan_Vertical_Slice.md` |

---

## Catatan Koordinasi Cepat
* **Keuntungan Struktur Tim Ini:** Karena Programmer hanya 1 orang (**Rahmansyah**), risiko *merge conflict* kode/script hampir nol. Desainer Game (**Amirun & Arya**) cukup berkoordinasi saat menyentuh file `.tscn` map atau meng-upload aset `.png` ke folder `assets/`.
* **Integrasi Mingguan:** Setiap minggu, hasil aset dari Desainer Game, audio dari Sound Designer, dan data dialog dari Konseptor diserahkan/di-push agar Programmer bisa langsung memasangnya ke *build* Godot.
