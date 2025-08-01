
```markdown
# 🤖 Prompt Siap Pakai untuk Cursor IDE - Aplikasi Perpajakan Terpadu

Berikut adalah daftar prompt untuk membantu kamu menyelesaikan setiap task menggunakan AI di Cursor IDE.

---

## 🔧 Modul PPh21

### 1. Form Input Data Karyawan
```

// Prompt:  
Buatkan class Python bernama `Karyawan` yang menyimpan data: nama, NPWP, gaji pokok, tunjangan, status kawin, dan PTKP. Tambahkan validasi agar NPWP harus 15 digit angka.

```

### 2. Fungsi Perhitungan PPh21 Berlapis
```

// Prompt:  
Buat fungsi `hitung_pph21(gaji_bulanan, status_kawin, ptkp)` yang menghitung PPh21 berdasarkan lapisan tarif (5%, 15%, dst.) dan pengurangan PTKP.

```

### 3. Export ke Excel dan PDF
```

// Prompt:  
Gunakan `pandas` untuk menyimpan daftar karyawan dan PPh21-nya ke dalam file Excel. Format kolom: Nama, NPWP, Gaji, Potongan, PPh21.

// Prompt:  
Gunakan `jinja2` + `pdfkit` untuk membuat template slip PPh21 dan export ke PDF.

```

### 4. Slip Pajak Per Karyawan
```

// Prompt:  
Buat template HTML slip PPh21 untuk satu karyawan. Isi: Nama, NPWP, Gaji, Potongan, PPh21. Tambahkan tombol cetak.

```

---

## 🔧 Modul PPN

### 1. Input Data Faktur
```

// Prompt:  
Buat model data untuk menyimpan transaksi faktur PPN. Field: nomor faktur, tanggal, jenis (penjualan/pembelian), nilai, status (masukan/keluaran).

```

### 2. Hitung Total PPN
```

// Prompt:  
Buat fungsi untuk menghitung PPN sebesar 11% dari nilai transaksi dan pisahkan masukan vs keluaran.

```

### 3. Laporan Bulanan
```

// Prompt:  
Buat fungsi untuk mengelompokkan transaksi PPN berdasarkan bulan dan menghitung total PPN keluaran dan masukan.

```

### 4. Export Jurnal Transaksi
```

// Prompt:  
Buat fungsi untuk menyimpan jurnal transaksi PPN ke file Excel, dengan format: tanggal, nomor faktur, jenis, nilai, PPN.

```

---

## 🔧 Modul SPT Tahunan

### 1. Input Penghasilan, Pengurang, Aset
```

// Prompt:  
Buat model data untuk mencatat penghasilan setahun, aset, dan pengurang. Gunakan dictionary atau class.

```

### 2. Kalkulasi PPh Final
```

// Prompt:  
Buat fungsi `hitung_pph_final(penghasilan_bersih)` menggunakan tarif UMKM (0.5%) atau tarif progresif.

```

### 3. Simulasi Tampilan SPT
```

// Prompt:  
Buat simulasi form SPT dalam tampilan tabel HTML menggunakan data pengguna.

```

### 4. Export PDF dan CSV eFiling
```

// Prompt:  
Export form simulasi SPT ke file PDF menggunakan `pdfkit`. Tambahkan fungsi export CSV sesuai format DJP.

```

---

## 🔧 Modul Dashboard

### 1. Ringkasan Data Semua Modul
```

// Prompt:  
Gabungkan data dari modul PPh21, PPN, dan SPT dalam satu fungsi yang mengembalikan ringkasan status laporan.

```

### 2. Grafik & Chart
```

// Prompt:  
Gunakan `matplotlib` untuk membuat grafik batang pengeluaran pajak bulanan berdasarkan data PPh21 dan PPN.

```

### 3. Notifikasi & Status
```

// Prompt:  
Buat sistem notifikasi sederhana (CLI/log/GUI) untuk mengingatkan tenggat pelaporan PPN dan SPT.

```

---

## 🔧 Modul Ekspor Laporan

### 1. Template Laporan (HTML)
```

// Prompt:  
Buat template laporan HTML yang bisa digunakan untuk PPh21, PPN, dan SPT. Gunakan Jinja2 dengan placeholder `{{ nama }}`, `{{ total_pph }}`.

```

### 2. Export PDF
```

// Prompt:  
Buat fungsi Python untuk merender template HTML Jinja2 menjadi file PDF menggunakan `pdfkit`.

```

### 3. Export Excel
```

// Prompt:  
Export laporan pajak per modul ke file Excel (`.xlsx`) menggunakan `pandas`.

```

---

## 🔧 GUI / Web Interface (Opsional)

### 1. Layout GUI
```

// Prompt:  
Buat layout GUI menggunakan `tkinter` dengan menu utama yang memiliki tombol akses ke modul PPh21, PPN, dan SPT.

```

### 2. Form Input & View
```

// Prompt:  
Buat form input data menggunakan `tkinter` untuk data karyawan (nama, gaji, tunjangan, NPWP) dan tampilkan tabel hasilnya.

```

### 3. Navigasi Modul
```

// Prompt:  
Buat navigasi tab di tkinter atau sidebar di Flask untuk mengakses masing-masing modul.

```

### 4. File Setting & Data Lokal
```

// Prompt:  
Simpan data konfigurasi pengguna (nama usaha, NPWP, alamat) dalam file `settings.json` dan load saat startup.

```

---

## ✅ Tips Penggunaan di Cursor
- Gunakan `// Prompt:` tepat di atas baris kode atau di file kosong
- Tekan `Cmd + I` / `Ctrl + I` untuk menjalankan AI Command
- Ulangi `Cmd + I` untuk refining atau revisi
```
