```markdown
# 📊 Aplikasi Perpajakan Terpadu untuk UMKM

Sebuah aplikasi berbasis Python yang membantu pelaku usaha menghitung, mencatat, dan mengelola kewajiban perpajakan seperti PPh21, PPN, dan pelaporan SPT Tahunan.

---

## 🧱 Struktur Fitur (Modular)

```

[ Dashboard Pajak ]  
|  
+-------+--------+---------+  
| | | |  
| PPh21 PPN SPT Tahunan  
| Karyawan Transaksi Perorangan / UMKM  
| Faktur  
|  
+-------------------------+  
| Reminder & Notifikasi  
| Export PDF / Excel

```

---

## 📐 Wireframe (Deskripsi Visual Kasar)

### 1. Halaman Dashboard
- [Total Pajak Dibayar Tahun Ini]
- [Ringkasan PPh21 Bulanan]
- [PPN Keluaran - PPN Masukan]
- [Status SPT Tahunan: Belum / Sudah Dilapor]
- Tombol:
  - [Hitung Pajak]
  - [Input Transaksi]
  - [Export Laporan]
  - [Pengaturan Data]

### 2. Modul PPh21
- Input: Nama, NPWP, Gaji Pokok, Tunjangan, Status Kawin
- Output: PPh21 Bulanan, Slip Pajak, Rekap Tahunan

### 3. Modul PPN
- Input: Tanggal, Jenis Transaksi, Nilai, Status Faktur
- Output: Total PPN Masukan & Keluaran, Saldo PPN, Jurnal

### 4. Modul SPT Tahunan
- Input: Penghasilan Neto, Pengurangan, Aset, Kewajiban
- Output: Form simulasi SPT, PDF Laporan, CSV eFiling

### 5. Reminder & Notifikasi
- Notifikasi jatuh tempo:
  - PPN bulanan (tgl 10-15)
  - PPh21 bulanan (tgl 15-20)
  - SPT Tahunan (Maret)

---

## ✅ Task Breakdown per Modul

### 🔧 Modul PPh21
- [ ] Buat form input data karyawan
- [ ] Fungsi perhitungan PPh21 berlapis
- [ ] Export hasil ke Excel dan PDF
- [ ] Slip pajak per karyawan

### 🔧 Modul PPN
- [ ] Input data faktur (penjualan/pembelian)
- [ ] Hitung total PPN keluaran dan masukan
- [ ] Laporan bulanan + saldo PPN
- [ ] Export jurnal transaksi

### 🔧 Modul SPT Tahunan
- [ ] Input penghasilan, pengurang, aset
- [ ] Kalkulasi otomatis PPh final
- [ ] Simulasi tampilan SPT
- [ ] Export PDF dan CSV eFiling

### 🔧 Modul Dashboard
- [ ] Ringkasan data dari semua modul
- [ ] Grafik & chart dengan matplotlib/plotly
- [ ] Notifikasi dan status pelaporan

### 🔧 Ekspor Laporan
- [ ] Buat template laporan dengan Jinja2
- [ ] Gunakan `pdfkit` atau `reportlab` untuk export PDF
- [ ] Ekspor Excel dengan `pandas` dan `openpyxl`

### 🔧 GUI (Opsional)
- [ ] Rancang layout GUI (Tkinter/PyQt/Web Flask)
- [ ] Form Input dan View Data
- [ ] Navigation antar modul
- [ ] File setting & penyimpanan data lokal (SQLite)

---

## 🧰 Teknologi & Library

- Python 3.x
- `pandas`, `openpyxl`, `jinja2`
- `matplotlib` / `plotly`
- `pdfkit` / `reportlab`
- `tkinter` atau `flask`
- SQLite (lokal) atau PostgreSQL (jika multi-user)

---

## 📁 Struktur Folder

```

aplikasi_pajak/  
├── app.py  
├── modules/  
│ ├── pph21.py  
│ ├── ppn.py  
│ ├── spt.py  
│ └── dashboard.py  
├── data/  
│ └── transaksi.csv  
├── reports/  
│ └── laporan_spt_2025.pdf  
├── templates/  
│ └── laporan.html  
├── gui/ (opsional)  
│ └── main_window.py  
└── README.md

```

---

## 💡 Pengembangan Selanjutnya

- [ ] Backup ke Google Drive atau Cloud
- [ ] Multi-user dengan login
- [ ] Sinkronisasi ke API DJP (opsional)
```
[[breakdown task aplikasi perpajakan terpadu]]
[[prompt untuk breakdown task aplikasi perpajakan terpadu]]
[[logic prompt aplikasi perpajakan terpadu]]
