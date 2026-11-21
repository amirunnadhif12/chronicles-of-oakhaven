# Brief & Checklist untuk Sound Designer
**Proyek:** Chronicles of Oakhaven (Vertical Slice — 5 Fase, 1 Karakter Utama)  
**Tujuan:** Acuan produksi musik (BGM), efek suara (SFX), dan spesifikasi teknis audio agar langsung siap masuk ke Godot 4 tanpa perlu *re-export* ulang.

---

## 1. Arahan Gaya Audio (Audio Direction)
Ciri khas audio game ini adalah **kontras emosional** antara kehangatan desa dan misteri ekspedisi:
* **Desa Oakhaven (Fase 1–3, Pagi/Siang):** Akustik *folk* yang hangat dan damai (gitar akustik, seruling kayu, piano lembut) ala *Stardew Valley*.
* **Hutan Whispering & Malam Terakhir (Fase 4–5):** Aransemen melankolis dan tegang (cello, piano minor, pad angin/kabut) ala *Clair Obscur*.
* **Pertarungan (Combat):** Musik lebih cepat dan berenergi agar mendukung fokus pemain saat melakukan *Reactive Parry*.

---

## 2. Daftar Kebutuhan BGM (Vertical Slice)
Semua BGM wajib dibuat **seamless loop** (saat diulang dari akhir ke awal tidak terdengar patah atau ada jeda hening):

| Nama File (`snake_case`) | Penggunaan di Game | Nuansa / Instrumen |
| :--- | :--- | :--- |
| `bgm_title_prologue.ogg` | Menu Utama & Prologue angka 27 | Piano lembut + cello melankolis, misterius |
| `bgm_oakhaven_day.ogg` | Eksplorasi Desa (Pagi–Sore) | Gitar akustik, seruling kayu, hangat & santai |
| `bgm_oakhaven_night.ogg` | Suasana Malam & Fase 5 di Kedai | Piano/string pelan, intim, emosional (perpisahan) |
| `bgm_whispering_forest.ogg` | Area luar (Pinggiran Hutan Whispering) | Atmosferik, tegang, suara angin/pad minor |
| `bgm_combat_battle.ogg` | Pertarungan Turn-Based + Mini-boss | Orkestra/perkusi dinamis, tempo jelas |

---

## 3. Daftar Kebutuhan SFX & Ambience
Fokus pada suara yang membuat interaksi terasa responsif (*game feel*), terutama untuk dialog, *Path Action*, dan *Reactive Parry*:

### A. Ambience (Looping `.ogg`)
* `amb_village_river.ogg` — Gemericik air sungai + kicau burung pelan.
* `amb_forest_mist.ogg` — Desau angin kabut hutan yang sunyi.

### B. Eksplorasi & Pergerakan (`.wav`)
* `sfx_step_grass_01.wav` *(buat 2–3 variasi)* — Langkah kaki di rumput.
* `sfx_step_wood_01.wav` *(buat 2–3 variasi)* — Langkah kaki di jembatan/lantai kayu.
* `sfx_step_stone_01.wav` *(buat 2–3 variasi)* — Langkah kaki di jalan batu.

### C. Dialog, Path Action, & Fase Cerita (`.wav`)
* `sfx_blip_hero.wav` — Suara ketikan dialog (*voice blip*) karakter utama.
* `sfx_blip_npc_low.wav` / `sfx_blip_npc_high.wav` — Variasi *voice blip* untuk NPC.
* `sfx_path_action_open.wav` — Suara membuka menu *Path Action* (`F`).
* `sfx_path_action_success.wav` & `sfx_path_action_fail.wav` — Feedback berhasil/gagal.
* `sfx_phase_unlock.wav` — Suara penanda emosional saat **Fase Baru terbuka**.

### D. Cozy Mechanics & UI (`.wav`)
* `sfx_forage_pick.wav` — Memetik herba/item di alam.
* `sfx_cook_sizzle.wav` — Suara memasak bekal di Base Camp.
* `sfx_ui_hover.wav` & `sfx_ui_click.wav` — Navigasi menu & tombol.
* `sfx_journal_open.wav` — Suara membuka buku/jurnal (`Tab`).

### E. Combat & Reactive Parry (`.wav`) — *Paling Krusial*
* `sfx_combat_slash.wav` — Serangan karakter utama.
* `sfx_enemy_telegraph.wav` — **Isyarat suara singkat** sebelum musuh menyerang (membantu pemain menebak timing *Parry*).
* `sfx_parry_success.wav` — Dentingan logam tajam yang memuaskan saat *Parry* berhasil.
* `sfx_shield_break.wav` — Suara perisai pecah saat musuh terkena status *Break*.
* `sfx_hit_damage.wav` — Suara terkena serangan (jika gagal parry).

---

## 4. Spesifikasi Teknis Wajib (Godot 4 & `TECH_SPEC.md`)
1. **Format File:**
   * **BGM & Ambience:** Export ke **`.ogg`** (Vorbis) agar ukuran file ringan.
   * **SFX:** Export ke **`.wav`** (16-bit, 44.1 kHz) agar tidak ada *lag/delay* saat diputar cepat.
2. **Potong Jeda Awal (*Trim Silence*):** Pastikan tidak ada ruang hening (0.1–0.5 detik) di awal file SFX—terutama untuk `sfx_parry_success.wav`, `sfx_ui_click.wav`, dan `sfx_step_*` supaya suara keluar instan saat tombol ditekan.
3. **Penamaan File:** Wajib `snake_case`, huruf kecil semua, tanpa spasi (sesuai tabel di atas).
4. **Keseimbangan Volume (*Loudness*):**
   * BGM dijaga sekitar **`-12 dB` s.d. `-14 dB`** agar tidak menenggelamkan suara SFX/dialog.
   * SFX dijaga sekitar **`-3 dB` s.d. `-6 dB`**.

---

## 5. Rekomendasi Tools Gratis (Jika Belum Ada)
* **Musik (DAW):** LMMS, BandLab, atau Cakewalk.
* **SFX Retro / Voice Blips:** **jsfxr** (berbasis web) atau **ChipTone**.
* **Potong, Normalisasi Volume, & Export `.ogg`/`.wav`:** **Audacity**.
