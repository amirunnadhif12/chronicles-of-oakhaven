# Usulan 3.1 Core Gameplay Loop & Batasan Vertical Slice
*Dokumen ini adalah draf acuan untuk didiskusikan bersama tim agar bagian yang masih kosong di GDD bisa langsung difiksasi.*

---

## 1. Usulan Isian GDD Bagian 3.1: Core Gameplay Loop

```text
[1. Pagi & Siang di Desa Oakhaven (Cozy & Sosial)]
   ├─ Foraging herba, memancing di sungai, & bantu rutinitas warga
   ├─ Gunakan Path Action (Tombol F) ke NPC → naikkan Expedition Bond
   └─ Dapatkan informasi rahasia, diskon, atau resep masakan
            │
            ▼
[2. Sore di Base Camp / Kedai (Persiapan Ekspedisi)]
   ├─ Masak bahan yang dikumpulkan → jadi bekal Heal / Buff Combat
   ├─ Atur komposisi tim aktif & baca jurnal ekspedisi terdahulu
   └─ Cek sisa waktu/hari sebelum keberangkatan
            │
            ▼
[3. Ekspedisi Wilayah Luar (Eksplorasi & Tactical Combat)]
   ├─ Jelajahi bioma luar & hadapi musuh (Turn-Based + Reactive Parry)
   ├─ Manfaatkan buff makanan & bonus pasif dari Expedition Bond
   └─ Kumpulkan material langka & catatan Expedition 28/29
            │
            ▼
[4. Kembali ke Desa (Progresi & Dampak Dunia)]
   ├─ Restorasi fasilitas desa (jembatan/kincir) pakai material ekspedisi
   ├─ Buka area foraging baru, dialog lanjutan NPC, & lanjut ke hari berikutnya
   └─ (Kembali ke langkah 1 hingga siap menuju Monolith di akhir Chapter 1)
```

### Penjelasan Singkat Koneksi Antar-Sistem (Untuk Dimasukkan ke GDD)
* **Cozy → Combat:** Hasil *foraging* dan memancing dimasak menjadi bekal pemulih HP/Stamina serta *buff* pertarungan. *Expedition Bond* dengan warga membuka bonus pasif di dalam combat.
* **Combat → Cozy:** Material dan jurnal yang didapat dari ekspedisi dipakai untuk merestorasi fasilitas Desa Oakhaven (misalnya memperbaiki jembatan untuk membuka spot memancing baru) dan memicu dialog lanjutan warga.

---

## 2. Template Kesepakatan Batasan Vertical Slice (Chapter 1: 45–60 Menit)
Silakan coret/ubah bagian dalam tanda kurung `[...]` sesuai hasil rapat tim:

| Aspek | Usulan Scope Vertical Slice | Keputusan Tim |
| :--- | :--- | :--- |
| **Arah Gerak Karakter** | **4 Arah** (Atas, Bawah, Kiri, Kanan-mirror) | `[Setuju 4 Arah / Tetap 8 Arah]` |
| **Jumlah Karakter Playable** | **1 Karakter Utama** (contoh: Aldric). Anggota Expedition 27 lainnya (5 orang) dijadikan **NPC** | **Fiks: 1 Karakter Utama** `[Pilih nama hero]` |
| **Peran & Jumlah NPC** | Anggota ekspedisi lain + warga kunci (**±6–8 NPC**). **Alur cerita utama berjalan lewat interaksi & quest NPC di setiap fase** | `[Sebutkan daftar NPC & perannya]` |
| **Sistem Alur Cerita (Fase)** | Setiap fase cerita (misal: Fase 1 Pengenalan Tanda 27 → Fase 2 Persiapan & Investigasi → Fase 3 Keberangkatan) memicu **perubahan dialog, quest, & kondisi NPC** | `[Setuju sistem fase NPC]` |
| **Musim & Waktu** | **1 Musim** (Semi/Gugur) dengan siklus **Pagi – Siang – Sore – Malam** | `[Setuju 1 Musim]` |
| **Area / Map** | **Desa Oakhaven** (Area Utama) + **1 Area Luar Awal** (Pinggiran Hutan Whispering) | `[Setuju / Tambah 1 area]` |
| **Aktivitas Cozy** | **Foraging + Memasak** (Wajib), **Memancing** (Opsional jika waktu cukup) | `[Pilih fitur wajib]` |
| **Combat & Musuh** | **Turn-Based (1 Hero) + Reactive Parry + Break** dengan **2 jenis musuh biasa + 1 mini-boss** | `[Setuju / Ubah jumlah]` |
| **Batas Waktu Act 1** | Berbasis **Progres Fase Cerita NPC** (selesai semua quest fase → lanjut ke fase berikutnya) | **Fiks: Berbasis Fase Cerita NPC** |

---

## 3. Contoh Alur 5 Fase Misi NPC (*Phase Progression*)
Struktur **5 Fase** sangat pas untuk durasi Vertical Slice (45–60 menit) karena alur emosinya naik bertahap dari hangat ke tegang, tanpa menambah beban aset baru (cukup manfaatkan map desa + 1 area luar):

* **Fase 1 — Munculnya Angka 27 (Prologue & Orientasi):**
  * *Misi NPC:* Bicara dengan Kepala Desa / anggota Expedition 27 di alun-alun untuk memahami situasi munculnya angka 27 di langit.
  * *Terbuka setelah selesai:* **Fase 2** (akses penuh ke area kebun, tepi sungai, dan Base Camp).
* **Fase 2 — Kehidupan Desa & Perbekalan (Cozy Mechanics):**
  * *Misi NPC:* Bantu Mira & warga mengumpulkan bahan (*foraging* herba / memancing) lalu memasak bekal pertama di Base Camp.
  * *Terbuka setelah selesai:* **Fase 3** (fitur *Path Action* `F` aktif penuh dan NPC tertentu mulai punya dialog lanjutan).
* **Fase 3 — Rahasia Jurnal Lama (Path Action & Investigasi):**
  * *Misi NPC:* Gunakan *Path Action* (`F`) kepada warga desa / penyintas untuk menggali informasi tersembunyi tentang ekspedisi terdahulu (Expedition 28/29).
  * *Terbuka setelah selesai:* **Fase 4** (gerbang jalur luar desa menuju pinggiran Hutan Whispering terbuka).
* **Fase 4 — Langkah Pertama ke Luar Lembah (Ekspedisi & Combat):**
  * *Misi NPC:* Uji jalur luar bersama tim di pinggiran Hutan Whispering, kalahkan musuh dengan *Reactive Parry & Break*, dan bawa pulang material/jurnal.
  * *Terbuka setelah selesai:* **Fase 5** (suasana desa berubah ke senja/malam menjelang keberangkatan).
* **Fase 5 — Malam Terakhir di Oakhaven (Klimaks Chapter 1 & Keberangkatan):**
  * *Misi NPC:* Gunakan material untuk restorasi kecil fasilitas desa, lalu hadiri momen perpisahan (*Expedition Bond*) bersama para NPC di Kedai *"The Golden Wheat"* sebelum berangkat.
  * *Terbuka setelah selesai:* **Penutup Vertical Slice Chapter 1** (transisi menuju Act 2).

