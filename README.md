# Engineering Economics Solver

Aplikasi web pembantu perhitungan Ekonomi Teknik. Versi awal berjalan lokal di browser dan tidak membutuhkan API berbayar.

## Fitur v1.0
- Single Payment (P/F)
- Uniform Series (P/A, A/P, F/A, A/F)
- Arithmetic Gradient (P/G dan F/G)
- Net Present Value (NPV)
- Annual Equivalent (AE)
- Nominal dan effective interest
- Input narasi dengan parser heuristik yang hasilnya wajib dikonfirmasi
- Tabel arus kas, langkah penyelesaian, salin jawaban, dan cetak

## Persyaratan
- Node.js 18 atau lebih baru
- npm

## Menjalankan di komputer
1. Ekstrak ZIP.
2. Buka folder proyek di VS Code atau terminal.
3. Jalankan:

```bash
npm install
npm run dev
```

4. Buka alamat lokal yang ditampilkan Vite, biasanya `http://localhost:5173`.

## Build untuk produksi

```bash
npm run build
npm run preview
```

Folder hasil build adalah `dist`.

## Deploy ke Vercel
1. Upload seluruh isi proyek ke repository GitHub.
2. Login ke Vercel menggunakan GitHub.
3. Import repository.
4. Framework preset: Vite.
5. Build command: `npm run build`.
6. Output directory: `dist`.
7. Klik Deploy.

## Catatan metode dan asumsi
- Semua arus kas NPV/AE terjadi pada akhir periode; tahun 0 tidak didiskontokan.
- Nominal positif = penerimaan; negatif = pengeluaran.
- Uniform Series menganggap pembayaran terjadi pada akhir periode.
- Gradient murni diasumsikan 0 pada periode pertama, G pada periode kedua.
- Tingkat bunga harus dinyatakan per periode yang sama dengan arus kas.
- Pada soal cicilan bulanan, masukkan bunga per bulan setelah menentukan konversi yang tepat dari bunga tahunan.
- AE menggunakan satu umur analisis yang diberikan. Perbandingan umur alternatif yang berbeda memerlukan pemilihan periode studi atau asumsi pengulangan/penggantian.
- Parser narasi hanya membantu menemukan kandidat angka dan indikasi metode. Ia bukan AI dan tidak menjamin pemetaan parameter benar. Konfirmasi data secara manual.
- Versi ini belum mencakup IRR, BCR, depresiasi, pajak, replacement, payback, sensitivitas, dan break-even.

## Struktur
- `src/engine.js`: fungsi perhitungan.
- `src/App.jsx`: antarmuka dan alur input/output.
- `src/styles.css`: desain responsif.
