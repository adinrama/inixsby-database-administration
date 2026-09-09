# Studi Kasus — Hari 3

## Tugas 1 — Stored Procedure `sp_daftar_peserta`
 
Buat stored procedure `sp_daftar_peserta` untuk mendaftarkan seorang peserta ke sesi kursus tertentu, dengan validasi:
 
1. **Validasi duplikasi** — tolak jika peserta tersebut **sudah terdaftar** pada kombinasi kursus & sesi yang sama.
2. **Validasi kuota** — tolak jika jumlah pendaftar pada sesi tersebut **sudah mencapai kuota maksimum** (gunakan asumsi kuota = 30 peserta/sesi, atau tambahkan kolom `kuota` pada tabel `sesi` sebagai pengembangan).
3. Jika kedua validasi lolos, lakukan `INSERT` ke tabel `pendaftar` di dalam blok transaksi (`START TRANSACTION` ... `COMMIT`).
4. Prosedur mengembalikan status hasil (`BERHASIL`/`GAGAL` beserta alasannya) lewat parameter `OUT`.

## Tugas 2 — Function `fn_rata_nilai`
 
Buat function `fn_rata_nilai(kode_kursus)` yang mengembalikan **rata-rata nilai** seluruh peserta pada kursus tersebut (gabungan semua sesi).
 
## Tugas 3 — Trigger Otomatis pada `pendaftar`
 
Buat trigger yang memperbarui `jumlah_peserta` pada tabel `sesi` secara otomatis, mencakup **dua** event:
- Setelah ada `INSERT` baru ke `pendaftar` (peserta bertambah).
- Setelah ada `DELETE` dari `pendaftar` (peserta berkurang/dibatalkan).

## Tugas 4 — Pengujian Skenario
 
Uji seluruh objek yang telah dibuat dengan skenario berikut, sertakan bukti (screenshot/log query):
 
1. Pendaftaran peserta baru yang **valid** → pastikan `sp_daftar_peserta` mengembalikan status **BERHASIL** dan trigger memperbarui `jumlah_peserta`.
2. Pendaftaran peserta yang **sudah terdaftar** di sesi yang sama → pastikan ditolak (status **GAGAL**, tidak ada baris baru di `pendaftar`).
3. Pendaftaran ke sesi yang **kuotanya sudah penuh** → pastikan ditolak dan gunakan `ROLLBACK` untuk memastikan tidak ada perubahan data yang tersimpan sebagian.
4. Panggil `fn_rata_nilai` untuk minimal dua kursus berbeda, bandingkan hasilnya dengan perhitungan manual dari data yang ada.

### Output Hari Ini (dikumpulkan sebagai portofolio)
 
- [ ] Skrip `sp_daftar_peserta` (stored procedure)
- [ ] Skrip `fn_rata_nilai` (function)
- [ ] Skrip trigger `AFTER INSERT` dan `AFTER DELETE` pada `pendaftar`
- [ ] Bukti pengujian seluruh skenario (termasuk skenario gagal dengan `ROLLBACK`)
---
