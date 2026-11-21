# Brief & Checklist untuk Konseptor / Narrative Designer
**Proyek:** Chronicles of Oakhaven (Vertical Slice — 5 Fase)  
**Tujuan:** Dokumen ini berisi daftar kebutuhan cerita dan ide yang harus disiapkan oleh Konseptor agar bisa langsung dipakai oleh **Programmer**, **Artist**, dan **UI Designer** tanpa kerja dua kali.

---

## 1. Penetapan 1 Karakter Utama & Anggota Lain (NPC)
Dari anggota *Expedition 27* di GDD awal, konseptor perlu menetapkan:
* **1 Karakter Utama (Playable):** Pilih 1 tokoh utama yang dikendalikan pemain (misal: *Aldric*). Tentukan kepribadian, gaya bicara, dan *Path Action* (`F`) utamanya.
* **5 Anggota Lain sebagai NPC:** Tentukan peran, sifat, dan lokasi mereka di Desa Oakhaven (misal: Mira menjaga pos logistik/toko, Lyra meracik herba, Garrick melatih pertahanan di gerbang, dll.). Mereka menjadi pemberi misi utama per fase dan sumber *Expedition Bond*.

---

## 2. Profil NPC Kunci (Total ±6–8 NPC)
Untuk setiap NPC (termasuk anggota ekspedisi yang jadi NPC & warga desa seperti Kepala Desa / Pemilik Kedai), buat data ringkas berikut:
* **Nama & Peran:** (Contoh: *Bram — Pemilik Kedai "The Golden Wheat"*)
* **Lokasi di Desa:** (Zona Tengah / Timur / Barat / Utara)
* **Latar Belakang Emosional:** Kaitannya dengan kutukan angka tahunan / *The Fading* (misal: kehilangan adik di Expedition 28).
* **Rahasia *Path Action* (`F`):** Informasi atau item khusus apa yang baru keluar jika pemain memakai *Path Action* ke NPC ini?

---

## 3. Rincian Misi per Fase (Fase 1 – Fase 5)
Untuk setiap fase dari **5 Fase** yang sudah disepakati, konseptor perlu mengisi:
1. **Ringkasan Cerita Fase:** Apa yang terjadi secara emosional di fase ini?
2. **Misi Utama Pembuka Fase:**
   * Pemberi misi (NPC siapa).
   * Tugas pemain (bicara ke siapa / kumpulkan item apa / kalahkan musuh apa).
   * Perubahan di desa setelah misi selesai (gerbang terbuka / suasana berubah ke senja / NPC pindah posisi).
3. **Misi Sampingan Opsional (*Expedition Bond*):** 1 misi kecil per fase untuk memperdalam hubungan dengan warga (tidak wajib untuk lanjut fase, tapi memberi bonus/cerita tambahan).

---

## 4. Naskah Dialog (Format Siap Masuk Godot)
Agar programmer tidak perlu mengetik ulang dari paragraf panjang, tulis naskah dialog dalam bentuk **Tabel (Google Sheets / Excel)** dengan kolom berikut:

| ID Dialog | Fase | NPC | Kondisi | Ekspresi Potret | Teks Dialog *(Maks. 2–3 baris)* |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `dlg_f1_bram_01` | 1 | Bram | Normal | `sad` | "Angka 27 sudah terlukis di langit... Sebentar lagi giliran kalian." |
| `dlg_f1_bram_pa` | 1 | Bram | Path Action Sukses | `surprised` | "Kau menemukan catatan adikku? Tunggu, biar kuceritakan..." |

> **Aturan Penting Ukuran Layar (`640x360`):**  
> Kotak dialog pixel art ukurannya terbatas. Usahakan **1 kotak dialog maksimal 2–3 kalimat pendek (±80–120 karakter)** supaya teks tidak meluber dan nyaman dibaca.

---

## 5. Daftar Konten Pendukung (Item, Jurnal, & Musuh)
* **Item & Resep Masak:** Nama + deskripsi 1 kalimat untuk ±3–5 herba/ikan dan ±3 masakan (contoh: *Sup Moonleaf — Menghangatkan tubuh & memulihkan 30 HP*).
* **Potongan Jurnal Ekspedisi Terdahulu (2–3 Catatan):** Teks pendek berisi misteri dari *Expedition 28 / 29* yang ditemukan di Fase 3 & 4.
* **Konsep 2–3 Jenis Musuh Awal:** Nama, bentuk/konsep visual untuk artist, dan latar singkat kenapa mereka ada di Hutan Whispering.

---

## 6. Moodboard Visual & Audio (Untuk Artist & Komposer)
Cukup kumpulkan **3–5 gambar referensi** + catatan singkat:
* **Suasana Desa (Fase 1–3):** Palet hangat, damai, cahaya pagi/sore (*Stardew Valley*).
* **Suasana Hutan & Malam Terakhir (Fase 4–5):** Palet dingin, berkabut, melankolis, kelopak cahaya (*Clair Obscur*).
