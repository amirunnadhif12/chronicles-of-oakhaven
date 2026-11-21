# Panduan Setup GitHub & Project Awal Godot 4
Ikuti langkah-langkah ini secara berurutan oleh **1 orang koordinator/lead programmer** terlebih dahulu, lalu anggota tim lain tinggal melakukan `git clone`.

---

## Bagian A: Setup Repository GitHub
1. Buat repository baru di GitHub (misal nama repo: `chronicles-of-oakhaven`).
2. Pilih **Private** atau **Public** sesuai kebutuhan tim, lalu centang **Add a README file**.
3. Pada pilihan **Add .gitignore**, pilih **`Godot`** *(penting agar folder cache `.godot/` tidak ikut ter-upload ke GitHub)*.
4. Clone repository ke komputer masing-masing menggunakan Git / GitHub Desktop:
   ```bash
   git clone https://github.com/<username>/chronicles-of-oakhaven.git
   ```

---

## Bagian B: Setup Project Awal Godot 4
1. Buka **Godot Engine 4** → klik **New** → pilih folder repository GitHub yang baru di-clone.
2. Pilih Renderer: **Compatibility** atau **Forward+** (untuk game 2D pixel art, **Compatibility** sudah sangat ringan dan aman di semua laptop tim).
3. Buat struktur folder dasar di dalam panel **FileSystem** Godot sesuai `TECH_SPEC.md` (`assets/`, `data/`, `scenes/`, `scripts/`).

---

## Bagian C: Pengaturan Wajib di `Project Settings`
Buka menu **Project → Project Settings** (aktifkan toggle *Advanced Settings* di pojok kanan atas jika ada opsi yang belum muncul):

### 1. Pengaturan Resolusi Pixel-Perfect (`640x360`)
* Masuk ke **Display → Window**:
  * **Viewport Width:** `640`
  * **Viewport Height:** `360`
  * **Window Width Override:** `1280` *(atau `1920` agar nyaman saat testing di layar laptop)*
  * **Window Height Override:** `720` *(atau `1080`)*
  * **Stretch → Mode:** `viewport`
  * **Stretch → Aspect:** `keep`
  * **Stretch → Scale Mode:** `integer`

### 2. Pengaturan Pixel Art Tajam (`Nearest`)
* Masuk ke **Rendering → Textures**:
  * **Canvas Textures → Default Texture Filter:** ubah dari `Linear` menjadi **`Nearest`**.

### 3. Pengaturan Input Map
* Masuk ke tab **Input Map**, lalu tambahkan seluruh *action* sesuai daftar di `TECH_SPEC.md` Bagian 6 (`move_up`, `move_down`, `move_left`, `move_right`, `interact`, `action_parry_run`, `path_action`, `menu_journal`, `switch_leader_prev`, `switch_leader_next`).

---

## Bagian D: Push Awal ke GitHub
Setelah semua setting di atas selesai:
1. Simpan project (`Ctrl + S`).
2. Commit dan push ke GitHub agar seluruh anggota tim bisa mulai bekerja dari fondasi yang sama:
   ```bash
   git add .
   git commit -m "chore: initial godot 4 project setup (640x360 pixel-perfect)"
   git push origin main
   ```
3. Anggota tim lain cukup menjalankan `git pull` (atau `git clone`), buka `project.godot` di Godot 4, dan langsung siap bekerja di scene masing-masing.
