# 🌱 Pomodoro & Grow

Pomodoro & Grow adalah aplikasi web produktivitas berbasis **Pomodoro Timer** yang menggabungkan teknik manajemen waktu dengan sistem gamifikasi pertumbuhan tanaman virtual.

Pengguna dapat membuat akun, menjalankan sesi fokus, mengambil waktu istirahat, mengembangkan tanaman berdasarkan jumlah sesi yang diselesaikan, serta melihat statistik dan riwayat aktivitas fokus. Seluruh data aplikasi disimpan secara lokal melalui `localStorage` pada browser.

> Proyek ini dikembangkan sebagai **Final Project Pemrograman Perangkat Web (PPW)**.

---

## ✨ Fitur Utama

### 🔐 Autentikasi Lokal

- Registrasi akun menggunakan nama, email, dan kata sandi.
- Validasi kata sandi minimal 6 karakter.
- Pencegahan penggunaan email yang sudah terdaftar.
- Login dan logout berbasis data `localStorage`.
- Navigasi menyesuaikan status autentikasi pengguna.
- Proteksi halaman timer dan koleksi untuk pengguna yang belum login.

### ⏱️ Pomodoro Timer

- Timer sesi fokus dengan kontrol mulai, jeda, lanjutkan, dan reset.
- Pergantian otomatis antara mode fokus dan istirahat.
- Informasi status timer ditampilkan secara dinamis.
- Notifikasi berbentuk toast ketika sesi fokus atau istirahat selesai.

### 🌱 Gamifikasi Pertumbuhan Tanaman

Setiap sesi fokus yang berhasil diselesaikan akan meningkatkan perkembangan tanaman virtual pengguna.

Tahapan pertumbuhan tanaman:

| Level | Progres |
|---|---|
| Level 0 | Pot siap ditanam |
| Level 1 | Benih telah ditanam |
| Level 2 | Tunas kecil muncul |
| Level 3 | Pohon mulai rindang |
| Level 4 | Pohon raksasa |
| Level 5 | Target tercapai dan pohon tumbuh di alam bebas |

Ilustrasi tanaman dibuat menggunakan **SVG dinamis** yang diperbarui berdasarkan jumlah sesi fokus pengguna.

### 📊 Koleksi dan Riwayat Sesi

- Menampilkan seluruh riwayat sesi fokus.
- Menampilkan tanggal dan waktu sesi.
- Menampilkan durasi dan status sesi.
- Menampilkan level tanaman pada setiap sesi.
- Ringkasan statistik berupa:
  - total sesi;
  - total menit fokus;
  - level tanaman;
  - jumlah sesi hari ini.
- Fitur untuk menghapus seluruh riwayat pengguna.

### 🎨 Antarmuka Responsif

- Desain responsif menggunakan Bootstrap 5.
- Gaya visual bertema pastel dan playful.
- Animasi pertumbuhan tanaman dan transisi elemen.
- Komponen antarmuka yang konsisten pada seluruh halaman.
- Dukungan tampilan desktop dan perangkat bergerak.

---

## 🛠️ Teknologi yang Digunakan

| Teknologi | Kegunaan |
|---|---|
| HTML5 | Struktur halaman web |
| CSS3 | Tampilan, animasi, dan komponen kustom |
| JavaScript | Autentikasi, timer, gamifikasi, serta pengelolaan data |
| Bootstrap 5.3 | Grid, komponen, dan responsivitas |
| Google Fonts | Tipografi menggunakan font Nunito |
| Local Storage API | Penyimpanan akun, sesi aktif, dan riwayat fokus |
| SVG | Visualisasi pertumbuhan tanaman |
| YouTube Embed | Video pengenalan teknik Pomodoro |

---

## 📁 Struktur Proyek

```text
pomodoro-and-grow/
├── index.html       # Halaman utama dan informasi aplikasi
├── register.html    # Halaman pendaftaran pengguna
├── login.html       # Halaman login pengguna
├── timer.html       # Timer Pomodoro dan gamifikasi tanaman
├── koleksi.html     # Statistik dan riwayat sesi fokus
├── styles.css       # Stylesheet bersama untuk seluruh halaman
└── README.md        # Dokumentasi proyek
```

---

## 🚀 Menjalankan Proyek

### 1. Clone Repository

```bash
git clone  https://github.com/mpnabil95/Web-Pomodoro-and-Grow.git
```

### 2. Masuk ke Direktori Proyek

```bash
cd Web-Pomodoro-and-Grow
```

### 3. Jalankan dengan Local Server

Proyek ini tidak memerlukan proses build atau instalasi package. Jalankan menggunakan salah satu metode berikut.

#### Menggunakan Visual Studio Code Live Server

1. Buka direktori proyek di Visual Studio Code.
2. Pasang ekstensi **Live Server**.
3. Klik kanan pada `index.html`.
4. Pilih **Open with Live Server**.

#### Menggunakan Python

```bash
python -m http.server 8000
```

Kemudian buka:

```text
http://localhost:8000
```

> Koneksi internet diperlukan untuk memuat Bootstrap, Google Fonts, dan video YouTube yang digunakan melalui CDN atau embed eksternal.

---

## 📖 Cara Menggunakan

1. Buka halaman utama aplikasi.
2. Pilih **Daftar** untuk membuat akun baru.
3. Masuk menggunakan email dan kata sandi yang telah didaftarkan.
4. Buka halaman **Mulai Fokus**.
5. Tekan tombol **Mulai** untuk menjalankan timer.
6. Gunakan tombol **Jeda**, **Lanjutkan**, atau **Reset** sesuai kebutuhan.
7. Setelah sesi fokus selesai, tanaman akan berkembang dan riwayat akan disimpan.
8. Buka halaman **Koleksi Saya** untuk melihat statistik dan riwayat sesi.

---

## 💾 Struktur Penyimpanan Data

Aplikasi menggunakan `localStorage` sebagai penyimpanan sisi klien.

| Key | Isi Data |
|---|---|
| `pomodoroUsers` | Daftar seluruh pengguna yang telah terdaftar |
| `activeUser` | Data pengguna yang sedang login |
| `history_<email>` | Riwayat sesi fokus milik pengguna tertentu |

Contoh objek pengguna:

```json
{
  "name": "Petani Kode",
  "email": "user@example.com",
  "password": "password123",
  "completedSessions": 3
}
```

Contoh data riwayat sesi:

```json
{
  "date": "26/7/2026, 10.30.00",
  "duration": 25,
  "status": "Berhasil"
}
```

---

## ⚙️ Konfigurasi Durasi Timer

Konfigurasi timer berada di dalam file `timer.html`.

Versi Pomodoro standar dapat menggunakan:

```javascript
const SESSION_DURATION = 25 * 60;
const BREAK_DURATION = 5 * 60;
```

Pada source code saat ini, durasi timer diatur untuk kebutuhan pengujian cepat:

```javascript
const SESSION_DURATION = 5;
const BREAK_DURATION = 2;
```

Ubah nilai tersebut sebelum aplikasi digunakan sebagai timer Pomodoro normal.

---

## 🔄 Alur Aplikasi

```text
Beranda
   │
   ├── Daftar
   │      └── Simpan akun ke localStorage
   │
   ├── Login
   │      └── Simpan pengguna aktif
   │
   ├── Timer Fokus
   │      ├── Selesaikan sesi
   │      ├── Tingkatkan level tanaman
   │      └── Simpan riwayat sesi
   │
   └── Koleksi
          ├── Tampilkan statistik
          ├── Tampilkan riwayat
          └── Hapus seluruh riwayat
```

---

## 🔒 Catatan Keamanan

Proyek ini merupakan aplikasi front-end untuk pembelajaran. Sistem autentikasi belum menggunakan server atau database.

Beberapa keterbatasannya:

- kata sandi disimpan dalam bentuk teks biasa di `localStorage`;
- data dapat dilihat atau diubah melalui Developer Tools browser;
- data hanya tersedia pada browser dan perangkat yang sama;
- penghapusan data browser akan menghapus akun dan riwayat;
- sistem ini tidak sesuai untuk penggunaan produksi atau penyimpanan data sensitif.

Untuk pengembangan produksi, gunakan backend, database, hashing kata sandi, autentikasi berbasis sesi atau token, validasi server-side, dan koneksi HTTPS.

---

## 🧪 Pengujian yang Disarankan

- Registrasi dengan akun baru.
- Registrasi menggunakan email yang sama.
- Validasi kata sandi kurang dari 6 karakter.
- Login dengan kredensial benar dan salah.
- Proteksi halaman saat belum login.
- Fungsi mulai, jeda, lanjutkan, dan reset timer.
- Pergantian mode fokus dan istirahat.
- Perubahan level serta ilustrasi tanaman.
- Penyimpanan riwayat untuk pengguna berbeda.
- Perhitungan statistik sesi.
- Penghapusan seluruh riwayat.
- Responsivitas navbar, form, timer, dan tabel.

---

## 🗺️ Pengembangan Selanjutnya

Beberapa peningkatan yang dapat dikembangkan:

- backend dan database;
- autentikasi yang lebih aman;
- pengaturan durasi fokus dan istirahat;
- mode long break;
- suara atau notifikasi browser;
- target fokus harian;
- grafik produktivitas;
- sinkronisasi data antarperangkat;
- pilihan jenis tanaman;
- tema gelap;
- Progressive Web App;
- pengujian otomatis.

---

## 🤝 Kontribusi

Kontribusi, saran, dan perbaikan dapat dilakukan melalui langkah berikut:

1. Fork repository.
2. Buat branch baru.

   ```bash
   git checkout -b feature/nama-fitur
   ```

3. Commit perubahan.

   ```bash
   git commit -m "feat: menambahkan nama fitur"
   ```

4. Push branch.

   ```bash
   git push origin feature/nama-fitur
   ```

5. Buat Pull Request.

---

<p align="center">
  Dibuat dengan 🌱 untuk membantu membangun kebiasaan fokus.
</p>
