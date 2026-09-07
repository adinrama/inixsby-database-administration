# Studi Kasus — Hari 1
# Ekstensi ERD & Normalisasi: Pembayaran Kursus SIMKUR
 
**Database Administration Essentials with MySQL**
*(Persiapan Sertifikasi BNSP – Skema Database Administrator)*
 
---
 
## Konteks Kasus
 
Pihak kampus ingin SIMKUR juga mencatat **pembayaran biaya kursus**. Setiap peserta yang terdaftar pada sebuah kursus (satu baris `Pendaftar`) dikenakan **biaya kursus** tertentu, dan boleh melunasinya dalam **satu atau beberapa kali cicilan/angsuran**.
 
Berikut adalah rekap pembayaran yang masih dicatat secara manual di spreadsheet (**belum ternormalisasi**):
 
| No Peserta | Nama Peserta | Kode Kursus | Nama Kursus | Biaya Kursus | Cicilan 1 (Tgl) | Cicilan 1 (Jumlah) | Cicilan 2 (Tgl) | Cicilan 2 (Jumlah) | Cicilan 3 (Tgl) | Cicilan 3 (Jumlah) |
|---|---|---|---|---|---|---|---|---|---|---|
| 101 | Harry Boga | ORA | Oracle Fundamental | 1.500.000 | 2026-09-01 | 500.000 | 2026-09-15 | 500.000 | 2026-09-30 | 500.000 |
| 102 | Bambang Surya | ORA | Oracle Fundamental | 1.500.000 | 2026-09-02 | 1.500.000 | — | — | — | — |
| 103 | Siti Rahayu | UXF | Unix Full Package | 2.000.000 | 2026-09-03 | 1.000.000 | 2026-09-20 | 1.000.000 | — | — |
| 104 | Ratu Godek | UXF | Unix Full Package | 2.000.000 | 2026-09-05 | 2.000.000 | — | — | — | — |
 
*(Untuk menyederhanakan latihan, diasumsikan setiap peserta pada tabel ini hanya mengambil satu kursus.)*
 
**Masalah yang terlihat sekilas:**
- Kolom cicilan **berulang** (Cicilan 1, 2, 3) — jika suatu saat ada peserta yang mencicil 5 kali, harus menambah kolom baru lagi (Cicilan 4, 5, ...). Ini adalah *repeating group* klasik.
- Banyak sel kosong (`—`) karena tidak semua peserta mencicil 3 kali → boros ruang.
- Data `Nama Kursus` dan `Biaya Kursus` berulang untuk setiap peserta yang mengambil kursus yang sama.
---
 
## Instruksi Pengerjaan
 
### Bagian A — Ekstensi ERD (± 10 menit)
 
Lihat kembali ERD SIMKUR yang sudah Anda rancang pada Tugas 1. Tambahkan entitas **Pembayaran**, dengan ketentuan:
 
1. Tentukan **attribute key** entitas `Pembayaran`.
2. Tentukan atribut lain yang relevan.
3. Tentukan apakah `Pembayaran` termasuk **strong entity** atau **weak entity**, dan jelaskan alasannya.
4. Tentukan **kardinalitas** relasi antara `Pendaftar` (dari ERD utama) dan `Pembayaran`.
### Bagian B — Normalisasi Data Pembayaran (± 10–15 menit)
 
Normalisasikan tabel rekap pembayaran di atas hingga **3NF**:
 
1. Identifikasi primary key dan seluruh ketergantungan fungsional (FD).
2. Ubah ke **1NF** — hilangkan *repeating group* kolom Cicilan 1/2/3.
3. Ubah ke **2NF** — hilangkan ketergantungan parsial.
4. Ubah ke **3NF** — hilangkan ketergantungan transitif.
5. Bandingkan hasil normalisasi Anda dengan hasil ekstensi ERD pada Bagian A — apakah keduanya konsisten?
---
