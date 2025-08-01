Berikut adalah file Markdown `logic_prompts.md` yang berisi kumpulan **prompt untuk membangun logika utama** dari seluruh project **Aplikasi Perpajakan Terpadu**. Prompt ini ditujukan untuk digunakan di **Cursor IDE** agar AI membantu membuat logika, alur data, dan perhitungan.

---

```markdown
# 🔍 Prompt Cursor IDE - Logika Inti Aplikasi Perpajakan Terpadu

Gunakan prompt berikut di Cursor IDE untuk membantu membangun logika dari aplikasi pajak terintegrasi yang terdiri dari: PPh21, PPN, SPT Tahunan, Dashboard, dan Ekspor Laporan.

---

## 🔁 Logika Umum

```

// Prompt:  
Buatkan struktur alur data untuk aplikasi pajak terintegrasi yang memuat modul: PPh21, PPN, SPT, Dashboard, dan Ekspor. Setiap modul harus bisa diakses dan saling berbagi data.

// Prompt:  
Rancang sistem penyimpanan data yang memungkinkan data karyawan, transaksi, dan laporan pajak disimpan terpisah tapi tetap dapat diakses lintas modul. Gunakan SQLite atau CSV.

```

---

## 📄 Logika Perhitungan PPh21

```

// Prompt:  
Buat logika lengkap perhitungan PPh21 bulanan berdasarkan gaji pokok, tunjangan, status kawin, dan PTKP. Gunakan lapisan tarif progresif (5%, 15%, 25%, 30%).

// Prompt:  
Tambahkan logika untuk membedakan wajib pajak TK/0, K/1, K/2, dst., dan menghitung PTKP sesuai peraturan pajak terbaru.

// Prompt:  
Implementasikan sistem rekapitulasi otomatis PPh21 tahunan berdasarkan data bulanan per karyawan.

```

---

## 🧾 Logika Perhitungan PPN

```

// Prompt:  
Buatkan logika untuk mencatat transaksi PPN dengan input: tanggal, nomor faktur, nilai transaksi, jenis (penjualan/pembelian), status (masukan/keluaran), dan nilai PPN.

// Prompt:  
Hitung selisih PPN Keluaran dan PPN Masukan per bulan. Tambahkan logika jurnal yang menyimpan kelebihan atau kekurangan bayar.

// Prompt:  
Buat filter untuk hanya menampilkan transaksi PPN bulan berjalan dan buat fungsi agregat bulanan.

```

---

## 📊 Logika Dashboard & Notifikasi

```

// Prompt:  
Rancang fungsi dashboard yang menarik data dari modul PPh21, PPN, dan SPT. Tampilkan dalam format ringkasan: total pajak bulan ini, status pelaporan, dan grafik pajak 12 bulan terakhir.

// Prompt:  
Buat logika reminder untuk tenggat waktu pajak: PPN setiap tanggal 10-15, PPh21 tanggal 15-20, SPT Tahunan sebelum 31 Maret.

// Prompt:  
Tambahkan fungsi logging aktivitas pengguna dan status pelaporan terakhir yang ditampilkan di dashboard.

```

---

## 📥 Logika Input Data (Form / CLI)

```

// Prompt:  
Buat logika form input data karyawan yang disimpan ke CSV/SQLite dan divalidasi sebelum digunakan untuk perhitungan PPh21.

// Prompt:  
Buat sistem input transaksi PPN dari CLI (Command Line Interface) dan otomatis disimpan ke database.

```

---

## 📤 Logika Export Laporan

```

// Prompt:  
Buatkan logika export laporan PPh21 bulanan dan tahunan ke PDF dan Excel. Gunakan template HTML untuk laporan dan convert ke PDF.

// Prompt:  
Buat satu fungsi yang bisa menggabungkan data dari seluruh modul dan menghasilkan laporan tahunan komprehensif yang bisa diekspor ke PDF.

```

---

## 📦 Logika Manajemen File & Data

```

// Prompt:  
Buatkan sistem pengelolaan file otomatis yang menyimpan laporan PDF ke folder `reports/` dan membuat subfolder berdasarkan tahun.

// Prompt:  
Buat fungsi load/save data dari dan ke file `settings.json`, `karyawan.csv`, dan `transaksi.csv` untuk menyimpan preferensi pengguna dan histori transaksi.

```

---

## 🧠 Logika Tambahan (Opsional)

```

// Prompt:  
Tambahkan fitur analisis tren pajak (misalnya: grafik peningkatan PPh21 atau pengeluaran PPN dalam 6 bulan terakhir).

// Prompt:  
Buat logika sederhana untuk mengenali anomali atau lonjakan pajak berdasarkan rata-rata historis (deteksi lonjakan pajak bulanan).

```

---

## 📌 Cara Penggunaan di Cursor IDE
- Gunakan `// Prompt:` sebelum baris kosong atau komentar kosong
- Tekan `Ctrl+I` (Windows/Linux) atau `Cmd+I` (Mac) untuk menjalankan AI
- Kamu bisa refine atau minta perbaikan langsung di editor setelah prompt dijalankan

---

```

---

Jika kamu ingin, saya bisa bantu menggabungkan semua file Markdown (`README.md`, `task_breakdown.md`, `cursor_prompts.md`, dan `logic_prompts.md`) menjadi satu dokumentasi proyek atau langsung generate starter project-nya. Mau?