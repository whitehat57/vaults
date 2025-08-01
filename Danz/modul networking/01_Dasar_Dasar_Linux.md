# Modul 1: Dasar-dasar Linux

## Pengenalan Linux

### Apa itu Linux? Sejarah Singkat dan Filosofi

Linux adalah sistem operasi *open-source* berbasis kernel Linux. Kernel ini pertama kali dirilis oleh Linus Torvalds pada tahun 1991. Berbeda dengan sistem operasi komersial seperti Windows atau macOS, Linux dikembangkan secara kolaboratif oleh komunitas global dan didistribusikan di bawah lisensi *General Public License* (GPL), yang berarti siapa pun bebas menggunakan, memodifikasi, dan mendistribusikannya.

Filosofi utama Linux adalah kebebasan dan keterbukaan. Ini mendorong inovasi, transparansi, dan kemampuan bagi pengguna untuk mengontrol penuh sistem mereka.

### Distribusi Linux Populer

Linux hadir dalam berbagai "distribusi" (sering disebut "distro"), yang merupakan bundel kernel Linux dengan perangkat lunak sistem, pustaka, alat, dan lingkungan desktop. Beberapa distro populer meliputi:

*   **Ubuntu:** Sangat populer untuk pemula dan penggunaan desktop, juga banyak digunakan di server dan cloud. Dikenal karena kemudahan penggunaan dan komunitas yang besar.
*   **Debian:** Fondasi bagi banyak distro lain (termasuk Ubuntu). Dikenal karena stabilitas dan keamanannya.
*   **CentOS/Red Hat Enterprise Linux (RHEL):** Sangat populer di lingkungan server dan perusahaan karena stabilitas, dukungan jangka panjang, dan fokus pada keamanan. CentOS adalah versi *community-driven* dari RHEL.
*   **Fedora:** Distro yang didukung Red Hat, sering menjadi tempat pengujian fitur-fitur baru sebelum masuk ke RHEL. Cocok untuk pengguna yang ingin fitur terbaru.
*   **Arch Linux:** Dikenal karena pendekatannya yang "rolling release" dan minimalis, memberikan pengguna kontrol penuh atas instalasi. Lebih cocok untuk pengguna berpengalaman.

### Mengapa Linux Penting dalam Networking dan Cybersecurity

Linux adalah tulang punggung internet dan infrastruktur modern. Berikut alasannya:

*   **Stabilitas dan Keandalan:** Linux dikenal sangat stabil dan dapat berjalan berbulan-bulan atau bahkan bertahun-tahun tanpa perlu *reboot*. Ini krusial untuk server jaringan dan sistem cloud yang harus selalu aktif.
*   **Keamanan:** Dengan model *open-source* dan komunitas yang aktif, celah keamanan seringkali ditemukan dan diperbaiki dengan cepat. Linux juga menawarkan kontrol granular atas izin file dan proses, yang penting untuk mengamankan sistem. Banyak alat *cybersecurity* (misalnya, Nmap, Wireshark, Metasploit) dikembangkan untuk dan berjalan optimal di Linux.
*   **Fleksibilitas dan Kustomisasi:** Linux dapat disesuaikan untuk berbagai kebutuhan, mulai dari server web ringan hingga superkomputer. Ini memungkinkan administrator jaringan dan profesional keamanan untuk membangun sistem yang sangat spesifik dan efisien.
*   **Dukungan Jaringan Bawaan:** Linux memiliki dukungan jaringan yang sangat kuat dan terintegrasi, menjadikannya pilihan utama untuk *router*, *firewall*, server DNS, dan berbagai layanan jaringan lainnya.
*   **Efisiensi Sumber Daya:** Linux dapat berjalan dengan baik pada perangkat keras dengan sumber daya terbatas, menjadikannya ideal untuk perangkat IoT, server kecil, atau mesin virtual di cloud.
*   **Alat Baris Perintah yang Kuat:** Sebagian besar konfigurasi dan administrasi di Linux dilakukan melalui baris perintah, yang sangat efisien untuk otomatisasi dan manajemen jarak jauh, keterampilan penting dalam networking dan cloud.

## Perintah Dasar Linux

Menguasai perintah dasar Linux adalah kunci untuk berinteraksi dengan sistem.

### Navigasi Direktori

*   `pwd` (Print Working Directory): Menampilkan lokasi direktori saat ini.
    ```bash
    pwd
    # Output: /home/user/documents
    ```
*   `ls` (List): Menampilkan daftar file dan direktori di lokasi saat ini.
    *   `ls -l`: Menampilkan detail (izin, pemilik, ukuran, tanggal).
    *   `ls -a`: Menampilkan semua file, termasuk yang tersembunyi (diawali dengan `.`).
    *   `ls -lh`: Menampilkan ukuran file dalam format yang mudah dibaca (Human-readable).
    ```bash
    ls
    # Output: file1.txt mydir anotherfile.jpg

    ls -l
    # Output:
    # -rw-r--r-- 1 user user 1024 Jul 27 10:00 file1.txt
    # drwxr-xr-x 2 user user 4096 Jul 27 10:05 mydir
    ```
*   `cd` (Change Directory): Berpindah antar direktori.
    *   `cd ..`: Pindah ke direktori induk.
    *   `cd ~`: Pindah ke direktori home pengguna.
    *   `cd /`: Pindah ke direktori root.
    *   `cd /path/to/directory`: Pindah ke direktori spesifik.
    ```bash
    cd mydir
    pwd
    # Output: /home/user/documents/mydir

    cd ..
    pwd
    # Output: /home/user/documents
    ```

### Manajemen File dan Direktori

*   `mkdir` (Make Directory): Membuat direktori baru.
    ```bash
    mkdir new_folder
    ```
*   `rmdir` (Remove Directory): Menghapus direktori kosong.
    ```bash
    rmdir empty_folder
    ```
*   `cp` (Copy): Menyalin file atau direktori.
    *   `cp file.txt /path/to/destination/`: Menyalin file.
    *   `cp -r folder /path/to/destination/`: Menyalin direktori secara rekursif.
    ```bash
    cp file1.txt file1_copy.txt
    cp -r mydir backup_mydir
    ```
*   `mv` (Move/Rename): Memindahkan atau mengganti nama file/direktori.
    ```bash
    mv file1.txt new_name.txt
    mv new_name.txt /path/to/another/folder/
    ```
*   `rm` (Remove): Menghapus file atau direktori.
    *   `rm file.txt`: Menghapus file.
    *   `rm -r folder`: Menghapus direktori dan isinya secara rekursif.
    *   `rm -rf folder`: Menghapus direktori dan isinya secara paksa (hati-hati!).
    ```bash
    rm old_file.txt
    rm -r backup_mydir
    ```
*   `touch`: Membuat file kosong baru atau memperbarui timestamp file yang sudah ada.
    ```bash
    touch new_empty_file.txt
    ```

### Melihat Isi File

*   `cat` (Concatenate): Menampilkan seluruh isi file ke standar output.
    ```bash
    cat mydocument.txt
    ```
*   `less`: Menampilkan isi file satu layar penuh pada satu waktu, memungkinkan *scrolling* maju dan mundur. Tekan `q` untuk keluar.
    ```bash
    less large_log_file.log
    ```
*   `more`: Mirip dengan `less`, tetapi hanya memungkinkan *scrolling* maju. Tekan `Space` untuk halaman berikutnya, `q` untuk keluar.
    ```bash
    more another_large_file.txt
    ```
*   `head`: Menampilkan beberapa baris pertama dari file (default: 10 baris).
    *   `head -n 5 file.txt`: Menampilkan 5 baris pertama.
    ```bash
    head mydocument.txt
    ```
*   `tail`: Menampilkan beberapa baris terakhir dari file (default: 10 baris). Berguna untuk melihat log yang sedang diperbarui.
    *   `tail -n 5 file.txt`: Menampilkan 5 baris terakhir.
    *   `tail -f logfile.log`: Mengikuti (follow) perubahan pada file log secara *real-time*.
    ```bash
    tail access.log
    ```

### Manajemen Izin File

Sistem izin file Linux sangat penting untuk keamanan. Setiap file dan direktori memiliki izin untuk tiga kategori: pemilik (owner), grup (group), dan lainnya (others). Izin ini adalah:

*   `r` (read): Membaca isi file atau melihat isi direktori.
*   `w` (write): Mengubah isi file atau membuat/menghapus file di direktori.
*   `x` (execute): Menjalankan file (jika itu program/script) atau masuk ke direktori.

Izin direpresentasikan dalam format simbolik (misalnya, `rwxr-xr-x`) atau numerik (oktal).

*   `chmod` (Change Mode): Mengubah izin file atau direktori.
    *   **Simbolik:**
        *   `u`: user (pemilik), `g`: group, `o`: others, `a`: all.
        *   `+`: menambah izin, `-`: menghapus izin, `=`: mengatur izin secara spesifik.
        ```bash
        chmod u+x myscript.sh      # Menambah izin eksekusi untuk pemilik
        chmod go-w myfile.txt      # Menghapus izin tulis untuk grup dan lainnya
        chmod a=rw- mydata.txt     # Mengatur izin baca/tulis untuk semua
        ```
    *   **Numerik (Oktal):** Setiap izin (r, w, x) memiliki nilai numerik: `r=4`, `w=2`, `x=1`. Jumlahkan nilai-nilai ini untuk setiap kategori.
        *   `7 (rwx)`: Baca, Tulis, Eksekusi
        *   `6 (rw-)`: Baca, Tulis
        *   `5 (r-x)`: Baca, Eksekusi
        *   `4 (r--)`: Baca
        ```bash
        chmod 755 myscript.sh      # Pemilik: rwx, Grup: r-x, Lainnya: r-x
        chmod 644 myfile.txt       # Pemilik: rw-, Grup: r--, Lainnya: r--
        ```
*   `chown` (Change Owner): Mengubah pemilik file atau direktori.
    ```bash
    chown newuser file.txt
    chown newuser:newgroup folder/ # Mengubah pemilik dan grup
    ```

## Manajemen Pengguna dan Grup

Mengelola pengguna dan grup adalah tugas dasar administrasi sistem Linux.

*   `useradd`: Membuat pengguna baru.
    *   `useradd -m username`: Membuat pengguna baru dan direktori home-nya.
    ```bash
    sudo useradd -m siswa1
    ```
*   `passwd`: Mengatur atau mengubah kata sandi pengguna.
    ```bash
    sudo passwd siswa1
    # Masukkan kata sandi baru
    ```
*   `userdel`: Menghapus pengguna.
    *   `userdel -r username`: Menghapus pengguna dan direktori home-nya.
    ```bash
    sudo userdel -r siswa1
    ```
*   `groupadd`: Membuat grup baru.
    ```bash
    sudo groupadd network_admins
    ```
*   `groupdel`: Menghapus grup.
    ```bash
    sudo groupdel network_admins
    ```
*   `usermod`: Memodifikasi properti pengguna.
    *   `usermod -aG groupname username`: Menambahkan pengguna ke grup tambahan.
    ```bash
    sudo usermod -aG sudo siswa1 # Menambahkan siswa1 ke grup sudo (izin admin)
    ```
*   `id`: Menampilkan informasi pengguna dan grup.
    ```bash
    id siswa1
    ```

## Manajemen Paket

Manajer paket adalah alat yang digunakan untuk menginstal, memperbarui, mengkonfigurasi, dan menghapus perangkat lunak di Linux.

### Pengenalan Manajer Paket

*   **APT (Advanced Package Tool):** Digunakan pada distribusi berbasis Debian (Ubuntu, Debian, Mint).
*   **YUM/DNF (Yellowdog Updater Modified / Dandified YUM):** Digunakan pada distribusi berbasis Red Hat (CentOS, Fedora, RHEL). DNF adalah penerus YUM.

### Instalasi, Pembaruan, dan Penghapusan Paket

**Untuk distribusi berbasis Debian (APT):**

*   `sudo apt update`: Memperbarui daftar paket yang tersedia dari repositori. Ini penting dilakukan sebelum menginstal atau memperbarui paket.
    ```bash
    sudo apt update
    ```
*   `sudo apt upgrade`: Memperbarui semua paket yang terinstal ke versi terbaru.
    ```bash
    sudo apt upgrade
    ```
*   `sudo apt install nama_paket`: Menginstal paket baru.
    ```bash
    sudo apt install net-tools # Contoh: menginstal alat jaringan
    ```
*   `sudo apt remove nama_paket`: Menghapus paket, tetapi file konfigurasi mungkin tetap ada.
    ```bash
    sudo apt remove net-tools
    ```
*   `sudo apt purge nama_paket`: Menghapus paket beserta file konfigurasinya.
    ```bash
    sudo apt purge net-tools
    ```
*   `sudo apt autoremove`: Menghapus paket-paket yang tidak lagi diperlukan (dependensi yang tidak terpakai).
    ```bash
    sudo apt autoremove
    ```

**Untuk distribusi berbasis Red Hat (YUM/DNF):**

*   `sudo dnf check-update` (atau `sudo yum check-update`): Memeriksa pembaruan yang tersedia.
*   `sudo dnf update` (atau `sudo yum update`): Memperbarui semua paket yang terinstal.
*   `sudo dnf install nama_paket` (atau `sudo yum install nama_paket`): Menginstal paket baru.
*   `sudo dnf remove nama_paket` (atau `sudo yum remove nama_paket`): Menghapus paket.

## Editor Teks

Editor teks berbasis terminal sangat penting untuk mengkonfigurasi sistem Linux, terutama di lingkungan server tanpa GUI.

### Penggunaan Dasar Nano

Nano adalah editor teks yang sederhana dan mudah digunakan, cocok untuk pemula.

*   `nano nama_file`: Membuka file untuk diedit. Jika file tidak ada, Nano akan membuatnya.
    ```bash
    nano myconfig.conf
    ```
*   **Perintah Dasar di Nano (ditampilkan di bagian bawah layar):**
    *   `Ctrl + O`: Menyimpan perubahan (Write Out).
    *   `Ctrl + X`: Keluar dari Nano. Jika ada perubahan yang belum disimpan, Nano akan bertanya apakah Anda ingin menyimpannya.
    *   `Ctrl + W`: Mencari teks.
    *   `Ctrl + K`: Memotong baris.
    *   `Ctrl + U`: Menempelkan baris.

### Penggunaan Dasar Vim

Vim (Vi IMproved) adalah editor teks yang sangat kuat dan efisien, tetapi memiliki kurva pembelajaran yang lebih curam. Vim memiliki dua mode utama:

1.  **Mode Normal (Command Mode):** Mode default saat membuka Vim. Digunakan untuk navigasi, menghapus, menyalin, dan menempel.
2.  **Mode Insert:** Digunakan untuk mengetik teks.

*   `vim nama_file`: Membuka file untuk diedit.
    ```bash
    vim myscript.sh
    ```
*   **Perintah Dasar di Vim:**
    *   **Dari Mode Normal ke Mode Insert:**
        *   `i`: Insert (masuk mode insert di posisi kursor).
        *   `a`: Append (masuk mode insert setelah posisi kursor).
        *   `o`: Open (masuk mode insert di baris baru di bawah).
    *   **Dari Mode Insert ke Mode Normal:**
        *   Tekan `Esc`.
    *   **Menyimpan dan Keluar (dari Mode Normal):**
        *   `:w`: Menyimpan file.
        *   `:q`: Keluar (jika tidak ada perubahan).
        *   `:wq` atau `ZZ`: Menyimpan dan keluar.
        *   `:q!`: Keluar tanpa menyimpan (memaksa).
    *   **Navigasi (di Mode Normal):**
        *   `h`: Kiri, `j`: Bawah, `k`: Atas, `l`: Kanan.
        *   `w`: Pindah ke awal kata berikutnya.
        *   `b`: Pindah ke awal kata sebelumnya.
        *   `0`: Pindah ke awal baris.
        *   `$`: Pindah ke akhir baris.
        *   `G`: Pindah ke akhir file.
        *   `gg`: Pindah ke awal file.
    *   **Menghapus (di Mode Normal):**
        *   `x`: Menghapus karakter di bawah kursor.
        *   `dd`: Menghapus seluruh baris.
        *   `dw`: Menghapus kata.

## Dasar-dasar Shell Scripting

Shell scripting adalah cara untuk mengotomatisasi tugas-tugas di Linux dengan menulis serangkaian perintah dalam sebuah file.

### Konsep Dasar Scripting

*   **Shebang:** Baris pertama dari setiap script shell harus dimulai dengan `#!` (disebut shebang), diikuti dengan path interpreter yang akan menjalankan script tersebut (misalnya, `/bin/bash`).
    ```bash
    #!/bin/bash
    ```
*   **Komentar:** Baris yang dimulai dengan `#` adalah komentar dan diabaikan oleh interpreter.
*   **Variabel:** Menyimpan nilai. Tidak ada spasi di sekitar tanda `=`.
    ```bash
    NAMA="Dunia"
    echo "Halo, $NAMA!"
    ```
*   **Input Pengguna:** Menggunakan perintah `read`.
    ```bash
    read -p "Masukkan nama Anda: " NAMA_PENGGUNA
    echo "Halo, $NAMA_PENGGUNA!"
    ```
*   **Kondisional (if-else):** Mengeksekusi kode berdasarkan kondisi.
    ```bash
    if [ "$NAMA_PENGGUNA" == "Admin" ]; then
        echo "Selamat datang, Admin!"
    else
        echo "Anda bukan Admin."
    fi
    ```
*   **Loop (for, while):** Mengulang eksekusi kode.
    ```bash
    for i in 1 2 3 4 5; do
        echo "Angka: $i"
    done

    COUNT=0
    while [ $COUNT -lt 3 ]; do
        echo "Hitungan: $COUNT"
        COUNT=$((COUNT + 1))
    done
    ```
*   **Eksekusi Script:** Berikan izin eksekusi (`chmod +x script.sh`) lalu jalankan (`./script.sh`).

### Contoh Script Sederhana: Backup Direktori

Script ini akan membuat arsip `.tar.gz` dari direktori yang ditentukan dan menyimpannya di lokasi backup.

```bash
#!/bin/bash

# Script untuk membuat backup direktori

# Variabel
SOURCE_DIR="/home/user/documents" # Direktori yang akan di-backup
BACKUP_DIR="/var/backups"         # Lokasi penyimpanan backup
DATE=$(date +%Y%m%d_%H%M%S)       # Format tanggal untuk nama file
BACKUP_FILE="backup_${DATE}.tar.gz" # Nama file backup

echo "Memulai proses backup..."

# Pastikan direktori backup ada
if [ ! -d "$BACKUP_DIR" ]; then
    echo "Direktori backup $BACKUP_DIR tidak ditemukan. Membuatnya..."
    sudo mkdir -p "$BACKUP_DIR"
    sudo chown $USER:$USER "$BACKUP_DIR" # Berikan izin ke pengguna saat ini
fi

# Membuat arsip tar.gz
tar -czvf "$BACKUP_DIR/$BACKUP_FILE" "$SOURCE_DIR"

# Memeriksa apakah backup berhasil
if [ $? -eq 0 ]; then
    echo "Backup berhasil dibuat: $BACKUP_DIR/$BACKUP_FILE"
else
    echo "Backup gagal!"
fi

echo "Proses backup selesai."
```

**Keterkaitan dengan Networking dan Cloud Computing:**

*   **Administrasi Jarak Jauh:** Perintah dasar Linux adalah fondasi untuk mengelola server jaringan dan instance cloud melalui SSH.
*   **Otomatisasi:** Shell scripting sangat penting untuk mengotomatisasi tugas-tugas seperti konfigurasi jaringan, deployment aplikasi di server cloud, atau pemantauan keamanan.
*   **Dasar Infrastruktur Cloud:** Sebagian besar server di cloud (VM atau kontainer) berjalan di atas Linux. Memahami dasar-dasarnya memungkinkan pengelolaan sumber daya cloud yang lebih efektif.
*   **Keamanan Sistem:** Pengetahuan tentang izin file, manajemen pengguna, dan alat dasar membantu mengamankan sistem Linux yang menjadi bagian dari infrastruktur jaringan atau cloud.

[[02_Konsep_Jaringan]]