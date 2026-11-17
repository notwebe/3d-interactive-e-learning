# 3D Top-Down Study Room & E-Learning Hub

Ruang belajar interaktif 3D bergaya *top-down isometric* dalam satu file HTML mandiri (*zero-build*). Dirancang sebagai pusat produktivitas kuliah yang menggabungkan eksplorasi ruangan 3D menggunakan **Three.js** dengan hub portal E-Learning, catatan mata kuliah, pelacak tugas & tenggat waktu, jam dinding & pencahayaan jendela real-time WIB, serta penyimpanan lokal berbasis `localStorage`.

---

## ✨ Fitur Utama

### 🎮 Eksplorasi Ruangan 3D & Kontrol
- **Pergerakan Hybrid (`WASD` / Panah & Click-to-Move):** Kendalikan karakter dengan keyboard (`W`, `A`, `S`, `D` atau `↑ ↓ ← →`), atau klik kiri lantai menggunakan mekanisme raycasting dengan indikator cincin *waypoint* bercahaya. Menekan tombol keyboard saat karakter sedang berjalan otomatis langsung mengembalikan kendali ke keyboard.
- **Interaksi Objek Langsung:** Dekati objek lalu tekan `E`, atau cukup klik kiri langsung objek 3D (karakter akan otomatis berjalan mendekat dan membuka panelnya).
- **Hover Glow & Label Melayang:** Label informasi objek 3D tersembunyi secara default agar ruangan tetap bersih, dan muncul mulus (*fade-in*) disertai efek *glow* & *scale* saat kursor diarahkan ke objek.
- **Kontrol Kamera Isometrik:** Putar sudut pandang ruangan dengan tombol `Q` / `R`, dan tutup panel modal kapan saja dengan `ESC`.

### 💻 Meja Komputer — *StudyOS Desktop Monitor*
- Antarmuka monitor desktop modern lengkap dengan ikon portal kuliah, jam sistem, dan *quick URL launcher*.
- **Anti-Blokir Jendela Mengambang (`1000×650 px`):** Mengklik portal atau mengetik URL akan membuka jendela *pop-up* berukuran khusus yang diposisikan tepat di tengah layar agar kompatibel dengan situs kampus yang membatasi `iframe` (`X-Frame-Options`).
- Tambah, edit, hapus, dan atur portal utama yang tersimpan otomatis di `localStorage`.

### 📚 Rak Buku Kuliah — Catatan Materi
- Ruang kerja 3 kolom untuk mengelola daftar **Mata Kuliah**, daftar **Bab / Materi**, dan **Editor Catatan** beserta *quick snippets* (`H2 Subjudul`, `Bullet`, `Highlight`, `Checklist`).
- Pencarian global instan lintas mata kuliah dan auto-save ke `localStorage`.

### 📋 Papan Tulis Tugas — To-Do List, Deadline & Auto-Import E-Learning
- Daftar tugas dengan status progres, filter (`Semua`, `Belum Selesai`, `Selesai`), pengurutan (`Tenggat Terdekat`, `Prioritas Tertinggi`, `Mata Kuliah`), dan ringkasan urgensi.
- **Auto-Import Tugas E-Learning (Anti-Duplikat)** dengan 3 cara praktis:
  1. **Upload File `.ics`:** Parser JavaScript membaca komponen `VEVENT` (`SUMMARY`, `DESCRIPTION`, `DTEND`/`DTSTART`).
  2. **Sinkronisasi Link iCal URL:** Simpan URL export kalender LMS (mis. Moodle) di `localStorage` dan sinkronkan lewat CORS proxy.
  3. **Smart Paste E-Learning:** Tempel teks mentah dari halaman Timeline LMS (Moodle, Google Classroom, SIAKAD) untuk mendeteksi judul tugas dan tanggal deadline (format Indonesia & Inggris) secara otomatis.

### 🕰️ Jam Dinding Real-Time WIB (`Asia/Jakarta`)
- Jam dinding 3D di sisi kiri ruangan dengan 3 jarum aktif (jam, menit, detik) yang bergerak real-time mengikuti waktu `Asia/Jakarta` (`UTC+7`), lengkap dengan indikator digital `HH:MM:SS WIB` di HUD dan label hover.

### 💡 Saklar Lampu Dinding (Mode Terang ↔ Mode Malam)
- Klik model 3D saklar lampu di dinding, klik tombol status di HUD, atau tekan tombol `L` untuk beralih mulus antara **Mode Terang** dan **Mode Malam**.
- Saat Mode Malam aktif, lampu utama meredup dan menyalakan pencahayaan hangat dari lampu meja belajar serta pendaran layar monitor dan papan tulis. Status lampu tersimpan di `localStorage`.

### 🪟 Jendela Kamar & Sinar Matahari Real-Time WIB
- Jendela 3D dengan kaca langit dinamis, berkas sinar volumetrik (*god rays*), dan pantulan petak cahaya di lantai yang berpadu mulus dengan Mode Terang/Malam serta berubah sesuai jam WIB:
  - **Pagi (`06:00–10:59 WIB`):** Sinar kuning hangat dengan sudut miring pagi.
  - **Siang (`11:00–14:59 WIB`):** Sinar putih-kuning cerah dengan sudut lebih tegak.
  - **Sore / Golden Hour (`15:00–17:59 WIB`):** Sinar jingga keemasan hangat yang memanjang di lantai.
  - **Malam (`18:00–05:59 WIB`):** Langit gelap berbintang dengan berkas sinar bulan biru yang tenang.

### 💾 Auto-Save & Cadangan Data JSON
- Seluruh data portal, catatan kuliah, dan daftar tugas tersimpan lokal di browser (`study_room_3d_hub_v1` dan `study_room_3d_lights_v1`).
- Tersedia tombol **Export JSON** dan **Import JSON** pada HUD pojok kanan atas untuk mencadangkan atau memindahkan data antar perangkat.

---

## ⌨️ Daftar Pintasan Kontrol

| Kontrol | Fungsi |
| --- | --- |
| `W` `A` `S` `D` atau `↑` `↓` `←` `→` | Menggerakkan karakter |
| Klik Kiri Lantai | Berjalan otomatis ke titik lantai (*Click-to-Move*) |
| Klik Kiri Objek | Menghampiri objek dan membuka panelnya (atau toggle saklar) |
| `E` | Membuka panel objek saat berada di zona interaktif |
| `L` | Menyalakan / mematikan lampu kamar (Mode Terang ↔ Mode Malam) |
| `Q` / `R` | Memutar kamera isometrik 3D |
| `ESC` | Menutup panel modal yang sedang terbuka |

---

## 🛠️ Teknologi yang Digunakan

- **HTML5 & Vanilla JavaScript** (single-file application, tanpa proses build)
- **[Three.js r128](https://threejs.org/)** (via CDN) untuk rendering 3D, pencahayaan, bayangan, dan *raycasting*
- **[Tailwind CSS](https://tailwindcss.com/)** (via CDN) untuk antarmuka HUD dan panel modal
- **Google Fonts** (`Plus Jakarta Sans` & `JetBrains Mono`)
- **Browser `localStorage` API** untuk persistensi data di sisi klien

---

## 🚀 Cara Menjalankan

Karena seluruh aplikasi berada di dalam satu file [`index.html`](index.html), Anda tidak perlu menginstal dependency apa pun:

1. Clone atau unduh repositori ini:
   ```bash
   git clone https://github.com/notwebe/3d-interactive-e-learning.git
   ```
2. Buka file [`index.html`](index.html) langsung di browser modern (Chrome, Edge, Firefox), atau jalankan menggunakan *local static server* (misalnya Live Server di VS Code).

> **Catatan:** Koneksi internet diperlukan saat pertama kali memuat library CDN (Three.js, Tailwind CSS, Google Fonts) serta saat menggunakan fitur Sinkronisasi iCal URL atau membuka portal E-Learning.
