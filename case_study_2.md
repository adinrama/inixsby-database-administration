# Studi Kasus — Hari 2

## Tugas 1 — Membangun Database SIMKUR
 
1. Buat database bernama **`simkur`** milik Anda sendiri.
2. Implementasikan seluruh tabel sesuai ERD/hasil normalisasi 3NF Hari 1 (`kursus`, `instruktur`, `sesi`, `peserta`, `pendaftar`), lengkap dengan:
   - Primary key (termasuk composite key pada `sesi` dan `pendaftar`)
   - Foreign key untuk menjaga referential integrity
   - Minimal satu constraint `NOT NULL`, satu `CHECK`, satu `DEFAULT`, dan satu `AUTO_INCREMENT`
3. *(Opsional)* Jika Hari 1 Anda menambahkan entitas `Instansi`, implementasikan juga tabelnya beserta foreign key dari `peserta`.

## Tugas 2 — Mengisi Data Dummy
 
Isi setiap tabel dengan **minimal 5–10 baris data dummy** (boleh memakai sebagian data contoh pada Bagian 2.3, atau membuat data sendiri), dengan syarat:
- Minimal ada **2 kursus yang punya sesi & pendaftar**, dan **minimal 1 kursus yang sengaja TIDAK diberi sesi sama sekali** (akan dipakai untuk Tugas 3 poin d).
- Minimal ada **1 peserta yang mendaftar ke lebih dari satu sesi/kursus**.

## Tugas 3 — Query Pelaporan
 
Tulis query SQL untuk memenuhi kebutuhan laporan berikut:
 
a. Daftar peserta per kursus & sesi (tampilkan nama kursus, nomor sesi, dan nama peserta).
b. Rata-rata dan nilai maksimum peserta per kursus.
c. Instruktur dengan honor tertinggi.
d. Kursus yang **belum memiliki sesi/peserta** (gunakan `LEFT JOIN`).
 
## Tugas 4 — Membuat View Pelaporan
 
Buat minimal **2 View**:
- `v_rekap_nilai` — rekap jumlah peserta, rata-rata nilai, dan nilai tertinggi per kursus & sesi.
- `v_daftar_peserta_kursus` — daftar lengkap peserta beserta kursus, sesi, instruktur, dan nilainya.

### Output Hari Ini (dikumpulkan sebagai portofolio)
 
- [ ] Skrip DDL (`CREATE DATABASE` + seluruh `CREATE TABLE`) database SIMKUR
- [ ] Skrip DML (`INSERT`) data dummy seluruh tabel
- [ ] Kumpulan query pelaporan (Tugas 3, poin a–d)
- [ ] Definisi 2 View pelaporan (Tugas 4)
---
