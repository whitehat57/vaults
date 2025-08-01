# 📝 Rincian Task Breakdown - Aplikasi Perpajakan Terpadu

Dokumen ini berisi penjabaran detail dari masing-masing modul dan tugas-tugas teknis yang perlu dikerjakan.

---

## 🔧 Modul PPh21

### 1. Form Input Data Karyawan
- [ ] Desain struktur data (Nama, NPWP, Gaji, Tunjangan, Status Kawin, PTKP)
- [ ] Implementasi input data (via CLI/GUI/Form Web)
- [ ] Validasi format NPWP dan angka

### 2. Fungsi Perhitungan PPh21 Berlapis
- [ ] Definisikan tarif berlapis PPh21 (5%, 15%, dst.)
- [ ] Buat fungsi pengurang: PTKP, BPJS, dsb
- [ ] Output nilai PPh bulanan dan tahunan

### 3. Export ke Excel dan PDF
- [ ] Format tabel rekap PPh21 per karyawan (bulanan)
- [ ] Gunakan `pandas.to_excel()` untuk ekspor Excel
- [ ] Gunakan `reportlab` atau `jinja2 + pdfkit` untuk PDF

### 4. Slip Pajak Per Karyawan
- [ ] Buat template slip pajak (PDF)
- [ ] Tampilkan detail: Nama, NPWP, Gaji, Potongan, PPh
- [ ] Export dan simpan per karyawan

---

## 🔧 Modul PPN

### 1. Input Data Faktur (Penjualan/Pembelian)
- [ ] Struktur data: No Faktur, Tanggal, Jenis, Nilai, Status (Keluaran/Masukan)
- [ ] Input form manual atau file Excel
- [ ] Validasi format faktur

### 2. Hitung Total PPN
- [ ] Fungsi hitung 11% dari nilai dasar
- [ ] Akumulasi total PPN Masukan & Keluaran
- [ ] Hitung selisih (PPN Dibayar)

### 3. Laporan Bulanan + Saldo
- [ ] Grouping data per bulan
- [ ] Ringkasan: jumlah transaksi, total PPN
- [ ] Saldo PPN = PPN keluaran - masukan

### 4. Export Jurnal Transaksi
- [ ] Format data transaksi pajak
- [ ] Ekspor ke Excel atau CSV

---

## 🔧 Modul SPT Tahunan

### 1. Input Penghasilan, Pengurang, Aset
- [ ] Form input data tahunan pribadi/UMKM
- [ ] Buat struktur aset dan utang
- [ ] Tambah fitur unggah CSV (opsional)

### 2. Kalkulasi PPh Final
- [ ] Gunakan tarif UMKM atau tarif progresif pribadi
- [ ] Hitung total penghasilan bersih
- [ ] Tentukan pajak terutang

### 3. Simulasi Tampilan SPT
- [ ] Tampilkan bentuk seperti form SPT 1770/1770S
- [ ] Tambahkan pengecekan isian wajib

### 4. Export PDF dan CSV eFiling
- [ ] Buat template HTML formulir
- [ ] Export ke PDF menggunakan `pdfkit`
- [ ] Export CSV sesuai format upload DJP

---

## 🔧 Modul Dashboard

### 1. Ringkasan Data dari Semua Modul
- [ ] Ambil data agregat dari PPh21, PPN, SPT
- [ ] Tampilkan rekap dan status (e.g., "Belum Lapor")

### 2. Grafik & Chart
- [ ] Gunakan `matplotlib` atau `plotly`
- [ ] Chart: Pajak per bulan, per jenis, per karyawan

### 3. Notifikasi & Status
- [ ] Reminder tanggal penting (via pop-up/log)
- [ ] Indikator status (e.g., “Terlambat”, “Lunas”)

---

## 🔧 Modul Ekspor Laporan

### 1. Template Laporan (HTML/Jinja2)
- [ ] Desain template HTML untuk PPh21, PPN, SPT
- [ ] Gunakan placeholder `{{}}` untuk data dinamis

### 2. Export PDF
- [ ] Konversi template HTML ke PDF (`pdfkit`)
- [ ] Simpan per laporan per bulan

### 3. Export Excel
- [ ] Format laporan dalam `pandas.DataFrame`
- [ ] Simpan sebagai `.xlsx` per modul

---

## 🔧 GUI (Opsional - Desktop/Web)

### 1. Layout GUI
- [ ] Gunakan `tkinter`, `PyQt`, atau `Flask` Web
- [ ] Desain layout per modul (Tab / Sidebar)

### 2. Form Input & View
- [ ] Input data dari user
- [ ] Tampilkan tabel, grafik, slip, dsb

### 3. Navigasi Modul
- [ ] Navigasi antar halaman utama (Dashboard, PPh21, PPN, SPT)
- [ ] Breadcrumb atau Tab Bar

### 4. File Setting & Data Lokal
- [ ] Simpan konfigurasi (e.g., path data, user info)
- [ ] Gunakan SQLite atau file `.json`

---

## 📌 Catatan Tambahan
- Gunakan Git untuk kontrol versi
- Simpan data dengan format terbuka (CSV/SQLite)
- Buat dokumentasi penggunaan akhir untuk user awam

