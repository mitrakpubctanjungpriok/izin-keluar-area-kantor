# 🚪 IZIN KELUAR AREA

## Sistem Absensi Digital MITRA KPU Bea Cukai Tanjung Priok

[![Deploy to Cloudflare Pages](https://img.shields.io/badge/Deploy-Cloudflare%20Pages-F38020?logo=cloudflare&logoColor=white)](https://pages.cloudflare.com/)
[![Google Sheets](https://img.shields.io/badge/Database-Google%20Sheets-34A853?logo=googlesheets&logoColor=white)](https://docs.google.com/spreadsheets)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)

![Preview](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![License](https://img.shields.io/badge/License-MIT-blue)

---

## 📋 Deskripsi

**Izin Keluar Area** adalah aplikasi web Single Page Application (SPA) untuk mengelola absensi izin keluar dan masuk karyawan PPNPN (Pegawai Pemerintah Non Pegawai Negeri) di lingkungan Bea Cukai Tanjung Priok.

Aplikasi ini memungkinkan:
- ✅ Karyawan mencatat izin keluar dengan validasi bertingkat
- ✅ Karyawan mencatat absen masuk dengan foto bukti
- ✅ Admin/PKD memantau riwayat absensi secara real-time
- ✅ Notifikasi email otomatis ke admin
- ✅ Export data ke CSV

---

## ✨ Fitur Utama

### 👤 Untuk Karyawan
| Fitur | Deskripsi |
|-------|-----------|
| 🚪 **Absen Keluar** | Form izin keluar dengan validasi izin pengawas, Subbag Turt, dan pegawai ruangan |
| 🚶 **Absen Masuk** | Absen masuk dengan foto barang bawaan |
| ⏰ **Jam Kerja** | Validasi waktu 06:00 - 18:00 |
| 📋 **Panduan** | Petunjuk penggunaan di bawah form |

### 👨‍💼 Untuk Admin
| Fitur | Deskripsi |
|-------|-----------|
| 📊 **Dashboard** | Statistik absensi (total, masuk, keluar, karyawan unik) |
| 📜 **Riwayat** | Tabel data dengan filter tanggal dan pencarian |
| 👥 **Kelola Karyawan** | Tambah, edit, hapus karyawan dengan ID |
| 📧 **Email Notifikasi** | Ubah email penerima notifikasi |
| 🔐 **Password** | Ubah password admin |
| 📥 **Export CSV** | Download data absensi |
| 🗑️ **Hapus Data** | Reset semua data absensi |

### 👮 Untuk PKD
| Fitur | Deskripsi |
|-------|-----------|
| 📜 **Riwayat** | Lihat dan filter data absensi |
| 🔐 **Password** | Ubah password PKD sendiri |
| 📥 **Export CSV** | Download data absensi |

---

## 🛠️ Teknologi

- **Frontend:** HTML5, Tailwind CSS, Vanilla JavaScript
- **Backend:** Google Apps Script
- **Database:** Google Sheets
- **Hosting:** Cloudflare Pages
- **Icons:** Lucide Icons

---

## 📊 Struktur Database (Google Sheets)

### Sheet "Absensi" (13 Kolom)
```
ID | Nama | Tipe | WaktuKeluar | WaktuMasuk | IzinPengawas | IzinSubbag | IzinPegawai | NamaPemberiIzin | Keperluan | Tanggal | Jam | Foto
```

### Sheet "Karyawan" (2 Kolom)
```
ID | Nama
```

### Sheet "Settings" (2 Kolom)
```
Type  | Value
admin | admin123
pkd   | pkd123
email | email@example.com
```

---

## 🚀 Cara Deploy

### Prasyarat
- Akun GitHub (gratis)
- Akun Cloudflare (gratis)
- Akun Google (untuk Google Sheets)

### Langkah 1: Setup Google Sheets

1. Buat Google Spreadsheet baru
2. Buat 3 sheet: `Absensi`, `Karyawan`, `Settings`
3. Isi header sesuai struktur di atas
4. Isi data karyawan di sheet "Karyawan"
5. Isi password default di sheet "Settings"

### Langkah 2: Setup Google Apps Script

1. Di Spreadsheet, klik **Extensions → Apps Script**
2. Hapus kode default, paste isi file `code.gs`
3. Klik **Deploy → New deployment**
4. Pilih **Web app**
5. Execute as: **Me**
6. Who has access: **Anyone**
7. Klik **Deploy**, copy URL

### Langkah 3: Update index.html

1. Buka file `index.html`
2. Cari baris: `const SCRIPT_URL = 'https://script.google.com/macros/s/YOUR_SCRIPT_ID/exec';`
3. Ganti `YOUR_SCRIPT_ID` dengan URL dari langkah 2

### Langkah 4: Upload ke GitHub

1. Login ke GitHub
2. Klik **+** → **New repository**
3. Nama: `izin-keluar-area`
4. Pilih **Public**
5. Klik **Create repository**
6. Klik **Add file → Upload files**
7. Upload `index.html`
8. Klik **Commit changes**

### Langkah 5: Deploy ke Cloudflare Pages

1. Login ke [Cloudflare Dashboard](https://dash.cloudflare.com)
2. Klik **Workers & Pages → Create application**
3. Pilih tab **Pages → Connect to Git**
4. Pilih repository `izin-keluar-area`
5. Klik **Begin setup**
6. Klik **Save and Deploy**
7. Tunggu 1-2 menit, website siap!

---

## 🔐 Login Default

| Role | Password |
|------|----------|
| Admin | `admin123` |
| PKD | `pkd123` |

> ⚠️ **Penting:** Segera ubah password setelah login pertama!

---

## 📧 Email Notifikasi

Setiap karyawan submit absensi, email otomatis dikirim dengan format:

**Subject:** `🚪 IZIN KELUAR - NAMA (ID: 123)` atau `✅ ABSEN MASUK - NAMA (ID: 123)`

**Isi Email:**
```
═══════════════════════════════════════════
       NOTIFIKASI ABSENSI PPNPN
   MITRA KPU BEA CUKAI TANJUNG PRIOK
═══════════════════════════════════════════

📋 DETAIL ABSENSI:
🆔 ID           : 2
👤 Nama         : AHMAD SYAIFUL
📅 Tanggal      : 18/12/2025
⏰ Jam Input    : 08:30:45
📌 Tipe         : KELUAR

🕐 Waktu Keluar : 08:30
🕐 Waktu Masuk  : 10:30

📝 STATUS IZIN:
• Izin Pengawas Lantai  : Ya
• Izin Subbag Turt      : Sudah
• Izin Pegawai Ruangan  : Sudah
• Pegawai Pemberi Izin  : PAK BUDI

📋 Keperluan    : BELI MAKAN
```

---

## 📁 Struktur File

```
izin-keluar-area/
├── index.html          # Aplikasi utama (SPA)
├── code.gs             # Google Apps Script
├── PANDUAN-SETUP.md    # Panduan setup lengkap
└── README.md           # Dokumentasi (file ini)
```

---

## 📱 Screenshot

### Halaman Utama
- Form absensi keluar dengan validasi
- Form absensi masuk dengan foto
- Status koneksi database

### Dashboard Admin
- Statistik absensi
- Tabel riwayat dengan filter
- Kelola karyawan (CRUD)
- Pengaturan email & password

---

## 🔧 Troubleshooting

### Popup Merah "Tidak Terhubung"
- Pastikan URL Google Apps Script sudah benar
- Pastikan sudah deploy sebagai Web App
- Pastikan "Who has access" = Anyone

### Dropdown Nama Kosong
- Isi Sheet "Karyawan" dengan data: `ID | Nama`
- Refresh website

### Email Tidak Terkirim
- Cek email di Sheet "Settings"
- Pastikan email valid
- Cek folder Spam

### Foto Tidak Muncul
- Pastikan foto di-compress (otomatis)
- Ukuran max: 400x400px, kualitas 50%

---

## 📄 Lisensi

MIT License - Silakan gunakan dan modifikasi sesuai kebutuhan.

---

## 👨‍💻 Kontributor

Dibuat **MUHAMMAD ALFINAS**

---

## 📞 Kontak

Jika ada pertanyaan atau masalah, hubungi Admin melalui email yang terdaftar di sistem.

---

<p align="center">
  <b>🇮🇩 Dibuat dengan ❤️ untuk Indonesia</b>
</p>
