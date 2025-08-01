# Modul 1: Dasar-dasar Linux

## Pengenalan Linux

### Apa itu Linux? Sejarah Singkat dan Filosofi

Linux adalah sistem operasi _open-source_ berbasis kernel Linux. Kernel ini pertama kali dirilis oleh Linus Torvalds pada tahun 1991. Berbeda dengan sistem operasi komersial seperti Windows atau macOS, Linux dikembangkan secara kolaboratif oleh komunitas global dan didistribusikan di bawah lisensi _General Public License_ (GPL), yang berarti siapa pun bebas menggunakan, memodifikasi, dan mendistribusikannya.

Filosofi utama Linux adalah kebebasan dan keterbukaan. Ini mendorong inovasi, transparansi, dan kemampuan bagi pengguna untuk mengontrol penuh sistem mereka.

### Distribusi Linux Populer

Linux hadir dalam berbagai "distribusi" (sering disebut "distro"), yang merupakan bundel kernel Linux dengan perangkat lunak sistem, pustaka, alat, dan lingkungan desktop. Beberapa distro populer meliputi:

- **Ubuntu:** Sangat populer untuk pemula dan penggunaan desktop, juga banyak digunakan di server dan cloud. Dikenal karena kemudahan penggunaan dan komunitas yang besar.
- **Debian:** Fondasi bagi banyak distro lain (termasuk Ubuntu). Dikenal karena stabilitas dan keamanannya.
- **CentOS/Red Hat Enterprise Linux (RHEL):** Sangat populer di lingkungan server dan perusahaan karena stabilitas, dukungan jangka panjang, dan fokus pada keamanan. CentOS adalah versi _community-driven_ dari RHEL.
- **Fedora:** Distro yang didukung Red Hat, sering menjadi tempat pengujian fitur-fitur baru sebelum masuk ke RHEL. Cocok untuk pengguna yang ingin fitur terbaru.
- **Arch Linux:** Dikenal karena pendekatannya yang "rolling release" dan minimalis, memberikan pengguna kontrol penuh atas instalasi. Lebih cocok untuk pengguna berpengalaman.

### Mengapa Linux Penting dalam Networking dan Cybersecurity

Linux adalah tulang punggung internet dan infrastruktur modern. Berikut alasannya:

- **Stabilitas dan Keandalan:** Linux dikenal sangat stabil dan dapat berjalan berbulan-bulan atau bahkan bertahun-tahun tanpa perlu _reboot_. Ini krusial untuk server jaringan dan sistem cloud yang harus selalu aktif.
- **Keamanan:** Dengan model _open-source_ dan komunitas yang aktif, celah keamanan seringkali ditemukan dan diperbaiki dengan cepat. Linux juga menawarkan kontrol granular atas izin file dan proses, yang penting untuk mengamankan sistem. Banyak alat _cybersecurity_ (misalnya, Nmap, Wireshark, Metasploit) dikembangkan untuk dan berjalan optimal di Linux.
- **Fleksibilitas dan Kustomisasi:** Linux dapat disesuaikan untuk berbagai kebutuhan, mulai dari server web ringan hingga superkomputer. Ini memungkinkan administrator jaringan dan profesional keamanan untuk membangun sistem yang sangat spesifik dan efisien.
- **Dukungan Jaringan Bawaan:** Linux memiliki dukungan jaringan yang sangat kuat dan terintegrasi, menjadikannya pilihan utama untuk _router_, _firewall_, server DNS, dan berbagai layanan jaringan lainnya.
- **Efisiensi Sumber Daya:** Linux dapat berjalan dengan baik pada perangkat keras dengan sumber daya terbatas, menjadikannya ideal untuk perangkat IoT, server kecil, atau mesin virtual di cloud.
- **Alat Baris Perintah yang Kuat:** Sebagian besar konfigurasi dan administrasi di Linux dilakukan melalui baris perintah, yang sangat efisien untuk otomatisasi dan manajemen jarak jauh, keterampilan penting dalam networking dan cloud.

### Struktur Direktori Linux

Sistem file Linux mengikuti hierarki standar yang disebut _Filesystem Hierarchy Standard_ (FHS). Memahami struktur ini penting untuk navigasi dan administrasi sistem:

- `/` (Root): Direktori utama dari seluruh sistem file
- `/home`: Direktori home untuk pengguna biasa (misalnya `/home/siswa1`)
- `/root`: Direktori home untuk pengguna root (administrator)
- `/bin`: Berisi perintah-perintah dasar yang diperlukan untuk sistem (ls, cp, mv, dll)
- `/usr/bin`: Berisi perintah-perintah untuk pengguna
- `/sbin`: Berisi perintah-perintah administratif sistem
- `/etc`: Berisi file konfigurasi sistem
- `/var`: Berisi data yang berubah-ubah (log, cache, spool)
- `/tmp`: Direktori untuk file sementara
- `/proc`: Sistem file virtual yang berisi informasi tentang proses dan kernel
- `/sys`: Sistem file virtual yang berisi informasi tentang perangkat keras
- `/dev`: Berisi file perangkat (device files)
- `/lib`: Berisi library yang diperlukan oleh program di /bin dan /sbin
- `/usr`: Berisi program, library, dan data untuk pengguna
- `/opt`: Direktori untuk software tambahan
- `/mnt` dan `/media`: Titik mount untuk perangkat penyimpanan

## Perintah Dasar Linux

Menguasai perintah dasar Linux adalah kunci untuk berinteraksi dengan sistem.

### Navigasi Direktori

- `pwd` (Print Working Directory): Menampilkan lokasi direktori saat ini.
    
    ```bash
    pwd
    # Output: /home/user/documents
    ```
    
- `ls` (List): Menampilkan daftar file dan direktori di lokasi saat ini.
    
    - `ls -l`: Menampilkan detail (izin, pemilik, ukuran, tanggal).
    - `ls -a`: Menampilkan semua file, termasuk yang tersembunyi (diawali dengan `.`).
    - `ls -lh`: Menampilkan ukuran file dalam format yang mudah dibaca (Human-readable).
    - `ls -la`: Kombinasi menampilkan semua file dengan detail.
    - `ls -R`: Menampilkan isi direktori secara rekursif.
    
    ```bash
    ls
    # Output: file1.txt mydir anotherfile.jpg
    
    ls -l
    # Output:
    # -rw-r--r-- 1 user user 1024 Jul 27 10:00 file1.txt
    # drwxr-xr-x 2 user user 4096 Jul 27 10:05 mydir
    ```
    
- `cd` (Change Directory): Berpindah antar direktori.
    
    - `cd ..`: Pindah ke direktori induk.
    - `cd ~`: Pindah ke direktori home pengguna.
    - `cd /`: Pindah ke direktori root.
    - `cd /path/to/directory`: Pindah ke direktori spesifik.
    - `cd -`: Pindah ke direktori sebelumnya.
    
    ```bash
    cd mydir
    pwd
    # Output: /home/user/documents/mydir
    
    cd ..
    pwd
    # Output: /home/user/documents
    ```
    
- `tree`: Menampilkan struktur direktori dalam bentuk pohon (perlu diinstal: `sudo apt install tree`).
    
    ```bash
    tree
    # Output:
    # .
    # ├── file1.txt
    # ├── mydir
    # │   └── subfile.txt
    # └── anotherfile.jpg
    ```
    

### Manajemen File dan Direktori

- `mkdir` (Make Directory): Membuat direktori baru.
    
    - `mkdir -p path/to/nested/directories`: Membuat direktori bersarang sekaligus.
    
    ```bash
    mkdir new_folder
    mkdir -p project/src/main/java
    ```
    
- `rmdir` (Remove Directory): Menghapus direktori kosong.
    
    ```bash
    rmdir empty_folder
    ```
    
- `cp` (Copy): Menyalin file atau direktori.
    
    - `cp file.txt /path/to/destination/`: Menyalin file.
    - `cp -r folder /path/to/destination/`: Menyalin direktori secara rekursif.
    - `cp -i file.txt backup.txt`: Menyalin dengan konfirmasi jika file tujuan sudah ada.
    - `cp -u source dest`: Menyalin hanya jika file sumber lebih baru.
    
    ```bash
    cp file1.txt file1_copy.txt
    cp -r mydir backup_mydir
    ```
    
- `mv` (Move/Rename): Memindahkan atau mengganti nama file/direktori.
    
    ```bash
    mv file1.txt new_name.txt
    mv new_name.txt /path/to/another/folder/
    ```
    
- `rm` (Remove): Menghapus file atau direktori.
    
    - `rm file.txt`: Menghapus file.
    - `rm -r folder`: Menghapus direktori dan isinya secara rekursif.
    - `rm -rf folder`: Menghapus direktori dan isinya secara paksa (hati-hati!).
    - `rm -i file.txt`: Menghapus dengan konfirmasi.
    
    ```bash
    rm old_file.txt
    rm -r backup_mydir
    ```
    
- `touch`: Membuat file kosong baru atau memperbarui timestamp file yang sudah ada.
    
    ```bash
    touch new_empty_file.txt
    touch -t 202307271200 file.txt  # Set waktu spesifik
    ```
    
- `ln` (Link): Membuat link ke file atau direktori.
    
    - `ln -s target linkname`: Membuat symbolic link (shortcut).
    - `ln target linkname`: Membuat hard link.
    
    ```bash
    ln -s /path/to/original/file.txt shortcut.txt
    ```
    
- `find`: Mencari file dan direktori berdasarkan kriteria.
    
    ```bash
    find /home -name "*.txt"           # Cari file .txt di /home
    find . -type d -name "project*"    # Cari direktori yang dimulai dengan "project"
    find . -size +100M                 # Cari file lebih besar dari 100MB
    find . -mtime -7                   # Cari file yang dimodifikasi dalam 7 hari terakhir
    ```
    
- `locate`: Mencari file dengan cepat menggunakan database (perlu `updatedb` untuk memperbarui).
    
    ```bash
    locate filename.txt
    sudo updatedb  # Perbarui database locate
    ```
    

### Melihat Isi File

- `cat` (Concatenate): Menampilkan seluruh isi file ke standar output.
    
    - `cat file1.txt file2.txt`: Menggabungkan dan menampilkan beberapa file.
    
    ```bash
    cat mydocument.txt
    ```
    
- `less`: Menampilkan isi file satu layar penuh pada satu waktu, memungkinkan _scrolling_ maju dan mundur. Tekan `q` untuk keluar.
    
    ```bash
    less large_log_file.log
    ```
    
- `more`: Mirip dengan `less`, tetapi hanya memungkinkan _scrolling_ maju. Tekan `Space` untuk halaman berikutnya, `q` untuk keluar.
    
    ```bash
    more another_large_file.txt
    ```
    
- `head`: Menampilkan beberapa baris pertama dari file (default: 10 baris).
    
    - `head -n 5 file.txt`: Menampilkan 5 baris pertama.
    
    ```bash
    head mydocument.txt
    ```
    
- `tail`: Menampilkan beberapa baris terakhir dari file (default: 10 baris). Berguna untuk melihat log yang sedang diperbarui.
    
    - `tail -n 5 file.txt`: Menampilkan 5 baris terakhir.
    - `tail -f logfile.log`: Mengikuti (follow) perubahan pada file log secara _real-time_.
    
    ```bash
    tail access.log
    ```
    
- `grep` (Global Regular Expression Print): Mencari pola teks dalam file.
    
    ```bash
    grep "error" logfile.txt           # Cari kata "error"
    grep -i "Error" logfile.txt        # Cari tanpa memperhatikan case
    grep -n "error" logfile.txt        # Tampilkan nomor baris
    grep -r "function" /path/to/code/  # Cari secara rekursif dalam direktori
    grep -v "debug" logfile.txt        # Tampilkan baris yang TIDAK mengandung "debug"
    ```
    
- `wc` (Word Count): Menghitung baris, kata, dan karakter dalam file.
    
    ```bash
    wc file.txt           # Tampilkan baris, kata, karakter
    wc -l file.txt        # Hitung baris saja
    wc -w file.txt        # Hitung kata saja
    ```
    
- `sort`: Mengurutkan isi file.
    
    ```bash
    sort names.txt        # Urutkan secara alfabetis
    sort -n numbers.txt   # Urutkan secara numerik
    sort -r file.txt      # Urutkan terbalik
    ```
    
- `uniq`: Menghapus baris duplikat yang berurutan.
    
    ```bash
    sort names.txt | uniq    # Hapus duplikat setelah diurutkan
    uniq -c file.txt         # Hitung kemunculan setiap baris
    ```
    

### Manajemen Izin File

Sistem izin file Linux sangat penting untuk keamanan. Setiap file dan direktori memiliki izin untuk tiga kategori: pemilik (owner), grup (group), dan lainnya (others). Izin ini adalah:

- `r` (read): Membaca isi file atau melihat isi direktori.
- `w` (write): Mengubah isi file atau membuat/menghapus file di direktori.
- `x` (execute): Menjalankan file (jika itu program/script) atau masuk ke direktori.

Izin direpresentasikan dalam format simbolik (misalnya, `rwxr-xr-x`) atau numerik (oktal).

- `chmod` (Change Mode): Mengubah izin file atau direktori.
    
    - **Simbolik:**
        
        - `u`: user (pemilik), `g`: group, `o`: others, `a`: all.
        - `+`: menambah izin, `-`: menghapus izin, `=`: mengatur izin secara spesifik.
        
        ```bash
        chmod u+x myscript.sh      # Menambah izin eksekusi untuk pemilik
        chmod go-w myfile.txt      # Menghapus izin tulis untuk grup dan lainnya
        chmod a=rw- mydata.txt     # Mengatur izin baca/tulis untuk semua
        ```
        
    - **Numerik (Oktal):** Setiap izin (r, w, x) memiliki nilai numerik: `r=4`, `w=2`, `x=1`. Jumlahkan nilai-nilai ini untuk setiap kategori.
        
        - `7 (rwx)`: Baca, Tulis, Eksekusi
        - `6 (rw-)`: Baca, Tulis
        - `5 (r-x)`: Baca, Eksekusi
        - `4 (r--)`: Baca
        
        ```bash
        chmod 755 myscript.sh      # Pemilik: rwx, Grup: r-x, Lainnya: r-x
        chmod 644 myfile.txt       # Pemilik: rw-, Grup: r--, Lainnya: r--
        chmod 600 secret.txt       # Hanya pemilik yang bisa baca/tulis
        ```
        
- `chown` (Change Owner): Mengubah pemilik file atau direktori.
    
    ```bash
    sudo chown newuser file.txt
    sudo chown newuser:newgroup folder/    # Mengubah pemilik dan grup
    sudo chown -R user:group directory/    # Ubah secara rekursif
    ```
    
- `chgrp` (Change Group): Mengubah grup pemilik file atau direktori.
    
    ```bash
    sudo chgrp developers project/
    ```
    
- `umask`: Mengatur izin default untuk file dan direktori yang baru dibuat.
    
    ```bash
    umask 022    # File baru: 644, Direktori baru: 755
    umask        # Lihat setting umask saat ini
    ```
    

## Manajemen Proses

Memahami dan mengelola proses adalah keterampilan penting dalam administrasi Linux.

### Melihat Proses yang Berjalan

- `ps` (Process Status): Menampilkan proses yang sedang berjalan.
    
    ```bash
    ps               # Proses milik pengguna saat ini
    ps aux           # Semua proses dengan detail lengkap
    ps -ef           # Format berbeda untuk semua proses
    ps -u username   # Proses milik pengguna tertentu
    ```
    
- `top`: Menampilkan proses secara real-time dengan penggunaan CPU dan memori.
    
    ```bash
    top
    # Tekan 'q' untuk keluar, 'k' untuk kill proses
    ```
    
- `htop`: Versi yang lebih interaktif dari `top` (perlu diinstal).
    
    ```bash
    sudo apt install htop
    htop
    ```
    
- `pgrep`: Mencari proses berdasarkan nama.
    
    ```bash
    pgrep firefox      # Cari PID proses firefox
    pgrep -u user      # Cari proses milik user tertentu
    ```
    

### Mengelola Proses

- `kill`: Menghentikan proses berdasarkan PID.
    
    ```bash
    kill 1234          # Hentikan proses dengan PID 1234
    kill -9 1234       # Paksa stop proses (SIGKILL)
    kill -15 1234      # Stop proses dengan normal (SIGTERM)
    ```
    
- `killall`: Menghentikan proses berdasarkan nama.
    
    ```bash
    killall firefox    # Hentikan semua proses firefox
    killall -9 chrome  # Paksa stop semua proses chrome
    ```
    
- `pkill`: Menghentikan proses berdasarkan pola nama.
    
    ```bash
    pkill -f "python script.py"    # Hentikan proses berdasarkan command line
    ```
    
- `jobs`: Melihat job yang berjalan di background.
    
    ```bash
    jobs               # Lihat job aktif
    ```
    
- `bg` dan `fg`: Memindahkan job antara background dan foreground.
    
    ```bash
    command &          # Jalankan di background
    bg %1              # Pindahkan job 1 ke background
    fg %1              # Pindahkan job 1 ke foreground
    ```
    
- `nohup`: Menjalankan perintah yang tidak akan terhenti saat terminal ditutup.
    
    ```bash
    nohup long-running-command &
    ```
    

## Manajemen Pengguna dan Grup

Mengelola pengguna dan grup adalah tugas dasar administrasi sistem Linux.

- `useradd`: Membuat pengguna baru.
    
    ```bash
    sudo useradd -m siswa1               # Buat user dengan home directory
    sudo useradd -m -s /bin/bash siswa2  # Buat user dengan shell bash
    sudo useradd -m -G sudo siswa3       # Buat user dan tambahkan ke grup sudo
    ```
    
- `passwd`: Mengatur atau mengubah kata sandi pengguna.
    
    ```bash
    sudo passwd siswa1    # Set password untuk siswa1
    passwd                # Ubah password sendiri
    ```
    
- `userdel`: Menghapus pengguna.
    
    ```bash
    sudo userdel siswa1      # Hapus user saja
    sudo userdel -r siswa1   # Hapus user dan home directory
    ```
    
- `groupadd`: Membuat grup baru.
    
    ```bash
    sudo groupadd network_admins
    sudo groupadd developers
    ```
    
- `groupdel`: Menghapus grup.
    
    ```bash
    sudo groupdel network_admins
    ```
    
- `usermod`: Memodifikasi properti pengguna.
    
    ```bash
    sudo usermod -aG sudo siswa1         # Tambahkan ke grup sudo
    sudo usermod -aG developers siswa1   # Tambahkan ke grup developers
    sudo usermod -s /bin/zsh siswa1      # Ubah shell default
    sudo usermod -l newname oldname      # Ubah nama login
    ```
    
- `id`: Menampilkan informasi pengguna dan grup.
    
    ```bash
    id siswa1        # Info lengkap tentang siswa1
    id -u siswa1     # UID saja
    id -g siswa1     # GID saja
    ```
    
- `who` dan `w`: Melihat pengguna yang sedang login.
    
    ```bash
    who              # Pengguna yang login
    w                # Info lebih detail termasuk aktivitas
    ```
    
- `su` dan `sudo`: Beralih pengguna atau menjalankan perintah sebagai pengguna lain.
    
    ```bash
    su - siswa1      # Beralih ke siswa1
    sudo command     # Jalankan command sebagai root
    sudo -u siswa1 command  # Jalankan command sebagai siswa1
    ```
    
- `groups`: Melihat grup yang dimiliki pengguna.
    
    ```bash
    groups           # Grup milik user saat ini
    groups siswa1    # Grup milik siswa1
    ```
    

## Manajemen Paket

Manajer paket adalah alat yang digunakan untuk menginstal, memperbarui, mengkonfigurasi, dan menghapus perangkat lunak di Linux.

### Pengenalan Manajer Paket

- **APT (Advanced Package Tool):** Digunakan pada distribusi berbasis Debian (Ubuntu, Debian, Mint).
- **YUM/DNF (Yellowdog Updater Modified / Dandified YUM):** Digunakan pada distribusi berbasis Red Hat (CentOS, Fedora, RHEL). DNF adalah penerus YUM.
- **Pacman:** Digunakan pada Arch Linux dan turunannya.
- **Zypper:** Digunakan pada openSUSE.

### Instalasi, Pembaruan, dan Penghapusan Paket

**Untuk distribusi berbasis Debian (APT):**

- `sudo apt update`: Memperbarui daftar paket yang tersedia dari repositori.
    
    ```bash
    sudo apt update
    ```
    
- `sudo apt upgrade`: Memperbarui semua paket yang terinstal ke versi terbaru.
    
    ```bash
    sudo apt upgradesudo apt full-upgrade  # Upgrade yang lebih agresif
    ```
    
- `sudo apt install nama_paket`: Menginstal paket baru.
    
    ```bash
    sudo apt install net-tools     # Alat jaringansudo apt install vim git curl  # Install beberapa paket sekaligus
    ```
    
- `sudo apt remove nama_paket`: Menghapus paket, tetapi file konfigurasi mungkin tetap ada.
    
    ```bash
    sudo apt remove net-tools
    ```
    
- `sudo apt purge nama_paket`: Menghapus paket beserta file konfigurasinya.
    
    ```bash
    sudo apt purge net-tools
    ```
    
- `sudo apt autoremove`: Menghapus paket-paket yang tidak lagi diperlukan.
    
    ```bash
    sudo apt autoremove
    ```
    
- `apt search keyword`: Mencari paket berdasarkan kata kunci.
    
    ```bash
    apt search editor
    ```
    
- `apt show nama_paket`: Menampilkan informasi detail tentang paket.
    
    ```bash
    apt show vim
    ```
    
- `apt list --installed`: Menampilkan semua paket yang terinstal.
    
    ```bash
    apt list --installed | grep vim
    ```
    

**Untuk distribusi berbasis Red Hat (YUM/DNF):**

- `sudo dnf check-update`: Memeriksa pembaruan yang tersedia.
- `sudo dnf update`: Memperbarui semua paket yang terinstal.
- `sudo dnf install nama_paket`: Menginstal paket baru.
- `sudo dnf remove nama_paket`: Menghapus paket.
- `dnf search keyword`: Mencari paket.
- `dnf info nama_paket`: Info detail paket.

### Manajemen Repository

- **Menambah repository (Ubuntu/Debian):**
    
    ```bash
    sudo add-apt-repository ppa:repository-name
    sudo apt update
    ```
    
- **Melihat repository yang aktif:**
    
    ```bash
    cat /etc/apt/sources.list
    ls /etc/apt/sources.list.d/
    ```
    

### Instalasi dari Source dan Package Manager Alternatif

- **Snap packages:**
    
    ```bash
    sudo snap install package-name
    sudo snap list
    sudo snap remove package-name
    ```
    
- **Flatpak:**
    
    ```bash
    sudo apt install flatpak
    flatpak install flathub com.application.name
    ```
    

## Sistem File dan Mount

### Melihat Informasi Disk dan Partisi

- `df`: Menampilkan penggunaan disk.
    
    ```bash
    df -h            # Human readable format
    df -i            # Info inode
    ```
    
- `du`: Menampilkan ukuran direktori.
    
    ```bash
    du -h /home      # Ukuran direktori /home
    du -sh *         # Ukuran semua item di direktori saat ini
    du -ah /var/log  # Ukuran semua file termasuk hidden
    ```
    
- `lsblk`: Menampilkan block devices dalam format tree.
    
    ```bash
    lsblk
    ```
    
- `fdisk`: Mengelola partisi disk.
    
    ```bash
    sudo fdisk -l    # List semua disk dan partisi
    ```
    

### Mount dan Unmount

- `mount`: Memasang filesystem.
    
    ```bash
    sudo mount /dev/sdb1 /mnt/usb         # Mount USB drive
    sudo mount -t ntfs /dev/sdb1 /mnt/windows  # Mount dengan filesystem type
    ```
    
- `umount`: Melepas filesystem.
    
    ```bash
    sudo umount /mnt/usb
    ```
    
- Konfigurasi automount di `/etc/fstab`:
    
    ```bash
    sudo nano /etc/fstab
    # Tambahkan baris seperti:
    # /dev/sdb1 /mnt/data ext4 defaults 0 2
    ```
    

## Jaringan di Linux

### Perintah Dasar Jaringan

- `ping`: Menguji konektivitas jaringan.
    
    ```bash
    ping google.com
    ping -c 4 8.8.8.8      # Ping 4 kali saja
    ping6 ipv6.google.com  # Ping menggunakan IPv6
    ```
    
- `wget` dan `curl`: Download file dari internet.
    
    ```bash
    wget https://example.com/file.zip
    curl -O https://example.com/file.zip    # Download dengan nama asli
    curl -L https://example.com/redirected  # Follow redirect
    ```
    
- `ssh`: Koneksi remote yang aman.
    
    ```bash
    ssh user@server.com
    ssh -p 2222 user@server.com  # Koneksi ke port khusus
    ```
    
- `scp`: Copy file melalui SSH.
    
    ```bash
    scp file.txt user@server:/remote/path/
    scp -r folder user@server:/remote/path/  # Copy direktori
    ```
    
- `rsync`: Sinkronisasi file yang efisien.
    
    ```bash
    rsync -avz /local/path/ user@server:/remote/path/
    ```
    

### Konfigurasi Jaringan

- `ip`: Perintah modern untuk konfigurasi jaringan.
    
    ```bash
    ip addr show        # Tampilkan alamat IP
    ip route show       # Tampilkan routing table
    ip link show        # Tampilkan network interfaces
    ```
    
- `ifconfig`: Perintah lama untuk konfigurasi interface (perlu net-tools).
    
    ```bash
    ifconfig            # Tampilkan semua interface
    ifconfig eth0       # Info interface tertentu
    ```
    
- `netstat`: Tampilkan koneksi jaringan.
    
    ```bash
    netstat -tuln       # TCP dan UDP listening ports
    netstat -r          # Routing table
    ```
    
- `ss`: Pengganti modern netstat.
    
    ```bash
    ss -tuln           # Listening ports
    ss -t -a           # Semua TCP connections
    ```
    

## Monitoring Sistem

### Monitoring Resource

- `free`: Menampilkan penggunaan memori.
    
    ```bash
    free -h            # Human readable
    free -s 2          # Update setiap 2 detik
    ```
    
- `uptime`: Menampilkan uptime dan load average.
    
    ```bash
    uptime
    ```
    
- `vmstat`: Statistik virtual memory.
    
    ```bash
    vmstat 2 5         # Update setiap 2 detik, 5 kali
    ```
    
- `iostat`: Statistik I/O (perlu sysstat package).
    
    ```bash
    sudo apt install sysstat
    iostat -x 2        # Extended info, update setiap 2 detik
    ```
    

### Log System

- `dmesg`: Menampilkan kernel messages.
    
    ```bash
    dmesg | tail           # 10 pesan terakhir
    dmesg | grep -i error  # Cari pesan error
    dmesg -w               # Follow mode (real-time)
    ```
    
- `journalctl`: Menampilkan log systemd.
    
    ```bash
    journalctl                    # Semua log
    journalctl -f                 # Follow mode
    journalctl -u ssh             # Log service tertentu
    journalctl --since "1 hour ago"  # Log 1 jam terakhir
    journalctl -p err             # Hanya error
    ```
    
- **File log penting:**
    
    ```bash
    tail -f /var/log/syslog       # System log umum
    tail -f /var/log/auth.log     # Authentication log
    tail -f /var/log/nginx/access.log  # Web server access log
    ```
    

## Manajemen Service (Systemd)

Systemd adalah sistem init dan service manager yang digunakan oleh sebagian besar distribusi Linux modern.

### Perintah Systemctl

- `systemctl status service_name`: Melihat status service.
    
    ```bash
    systemctl status ssh
    systemctl status nginx
    ```
    
- `systemctl start/stop/restart service_name`: Mengelola service.
    
    ```bash
    sudo systemctl start nginx
    sudo systemctl stop nginx
    sudo systemctl restart nginx
    sudo systemctl reload nginx    # Reload konfigurasi tanpa restart
    ```
    
- `systemctl enable/disable service_name`: Enable/disable service saat boot.
    
    ```bash
    sudo systemctl enable nginx   # Jalankan otomatis saat boot
    sudo systemctl disable nginx  # Jangan jalankan saat boot
    ```
    
- `systemctl list-units`: Melihat semua unit yang aktif.
    
    ```bash
    systemctl list-units --type=service  # Hanya service
    systemctl list-units --failed        # Hanya yang gagal
    ```
    
- `systemctl daemon-reload`: Reload konfigurasi systemd setelah perubahan.
    
    ```bash
    sudo systemctl daemon-reload
    ```
    

### Membuat Service Custom

Contoh membuat service sederhana:

```bash
sudo nano /etc/systemd/system/myapp.service
```

Isi file service:

```ini
[Unit]
Description=My Custom Application
After=network.target

[Service]
Type=simple
User=www-data
WorkingDirectory=/opt/myapp
ExecStart=/opt/myapp/start.sh
Restart=always

[Install]
WantedBy=multi-user.target
```

Kemudian aktifkan:

```bash
sudo systemctl daemon-reload
sudo systemctl enable myapp
sudo systemctl start myapp
```

## Keamanan Dasar Linux

### Firewall dengan UFW

UFW (Uncomplicated Firewall) adalah interface yang mudah untuk iptables.

- **Mengaktifkan UFW:**
    
    ```bash
    sudo ufw enable
    sudo ufw status
    ```
    
- **Aturan dasar:**
    
    ```bash
    sudo ufw default deny incoming   # Blokir semua koneksi masuk
    sudo ufw default allow outgoing  # Izinkan semua koneksi keluar
    ```
    
- **Membuka port tertentu:**
    
    ```bash
    sudo ufw allow 22                # SSH
    sudo ufw allow 80                # HTTP
    sudo ufw allow 443               # HTTPS
    sudo ufw allow from 192.168.1.0/24  # Izinkan dari subnet tertentu
    ```
    
- **Menghapus aturan:**
    
    ```bash
    sudo ufw status numbered         # Lihat nomor aturan
    sudo ufw delete 2                # Hapus aturan nomor 2
    ```
    

### SSH Hardening

- **Konfigurasi SSH yang lebih aman:**
    
    ```bash
    sudo nano /etc/ssh/sshd_config
    ```
    
    Pengaturan yang disarankan:
    
    ```bash
    Port 2222                    # Ubah port default
    PermitRootLogin no          # Larang login root
    PasswordAuthentication no   # Gunakan key-based auth
    AllowUsers username         # Hanya user tertentu yang boleh SSH
    ```
    
- **Generate SSH key pair:**
    
    ```bash
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```
    
- **Copy public key ke server:**
    
    ```bash
    ssh-copy-id user@server.com
    ```
    

### Fail2Ban

Fail2Ban melindungi dari brute force attack.

- **Instalasi:**
    
    ```bash
    sudo apt install fail2ban
    ```
    
- **Konfigurasi:**
    
    ```bash
    sudo nano /etc/fail2ban/jail.local
    ```
    
    Contoh konfigurasi:
    
    ```ini
    [DEFAULT]
    bantime = 3600
    findtime = 600
    maxretry = 3
    
    [sshd]
    enabled = true
    port = ssh
    filter = sshd
    logpath = /var/log/auth.log
    maxretry = 3
    ```
    

## Editor Teks

Editor teks berbasis terminal sangat penting untuk mengkonfigurasi sistem Linux, terutama di lingkungan server tanpa GUI.

### Penggunaan Dasar Nano

Nano adalah editor teks yang sederhana dan mudah digunakan, cocok untuk pemula.

- `nano nama_file`: Membuka file untuk diedit. Jika file tidak ada, Nano akan membuatnya.
    
    ```bash
    nano myconfig.conf
    ```
    
- **Perintah Dasar di Nano (ditampilkan di bagian bawah layar):**
    - `Ctrl + O`: Menyimpan perubahan (Write Out).
    - `Ctrl + X`: Keluar dari Nano. Jika ada perubahan yang belum disimpan, Nano akan bertanya apakah Anda ingin menyimpannya.
    - `Ctrl + W`: Mencari teks.
    - `Ctrl + K`: Memotong baris.
    - `Ctrl + U`: Menempelkan baris.
    - `Ctrl + G`: Bantuan (Help).
    - `Ctrl + C`: Menampilkan posisi kursor.
    - `Alt + U`: Undo perubahan terakhir.
    - `Alt + E`: Redo perubahan.

### Penggunaan Dasar Vim

Vim (Vi IMproved) adalah editor teks yang sangat kuat dan efisien, tetapi memiliki kurva pembelajaran yang lebih curam. Vim memiliki beberapa mode:

1. **Mode Normal (Command Mode):** Mode default saat membuka Vim. Digunakan untuk navigasi, menghapus, menyalin, dan menempel.
2. **Mode Insert:** Digunakan untuk mengetik teks.
3. **Mode Visual:** Untuk memilih teks.
4. **Mode Command-line:** Untuk perintah seperti save, quit, search.

- `vim nama_file`: Membuka file untuk diedit.
    
    ```bash
    vim myscript.sh
    ```
    
- **Perintah Dasar di Vim:**
    
    - **Dari Mode Normal ke Mode Insert:**
        - `i`: Insert (masuk mode insert di posisi kursor).
        - `a`: Append (masuk mode insert setelah posisi kursor).
        - `o`: Open (masuk mode insert di baris baru di bawah).
        - `O`: Open (masuk mode insert di baris baru di atas).
        - `s`: Substitute (hapus karakter dan masuk insert mode).
    - **Dari Mode Insert ke Mode Normal:**
        - Tekan `Esc`.
    - **Menyimpan dan Keluar (dari Mode Normal):**
        - `:w`: Menyimpan file.
        - `:q`: Keluar (jika tidak ada perubahan).
        - `:wq` atau `ZZ`: Menyimpan dan keluar.
        - `:q!`: Keluar tanpa menyimpan (memaksa).
        - `:x`: Simpan dan keluar (hanya jika ada perubahan).
    - **Navigasi (di Mode Normal):**
        - `h`: Kiri, `j`: Bawah, `k`: Atas, `l`: Kanan.
        - `w`: Pindah ke awal kata berikutnya.
        - `b`: Pindah ke awal kata sebelumnya.
        - `0`: Pindah ke awal baris.
        - `# Modul 1: Dasar-dasar Linux

## Pengenalan Linux

### Apa itu Linux? Sejarah Singkat dan Filosofi

Linux adalah sistem operasi _open-source_ berbasis kernel Linux. Kernel ini pertama kali dirilis oleh Linus Torvalds pada tahun 1991. Berbeda dengan sistem operasi komersial seperti Windows atau macOS, Linux dikembangkan secara kolaboratif oleh komunitas global dan didistribusikan di bawah lisensi _General Public License_ (GPL), yang berarti siapa pun bebas menggunakan, memodifikasi, dan mendistribusikannya.

Filosofi utama Linux adalah kebebasan dan keterbukaan. Ini mendorong inovasi, transparansi, dan kemampuan bagi pengguna untuk mengontrol penuh sistem mereka.

### Distribusi Linux Populer

Linux hadir dalam berbagai "distribusi" (sering disebut "distro"), yang merupakan bundel kernel Linux dengan perangkat lunak sistem, pustaka, alat, dan lingkungan desktop. Beberapa distro populer meliputi:

- **Ubuntu:** Sangat populer untuk pemula dan penggunaan desktop, juga banyak digunakan di server dan cloud. Dikenal karena kemudahan penggunaan dan komunitas yang besar.
- **Debian:** Fondasi bagi banyak distro lain (termasuk Ubuntu). Dikenal karena stabilitas dan keamanannya.
- **CentOS/Red Hat Enterprise Linux (RHEL):** Sangat populer di lingkungan server dan perusahaan karena stabilitas, dukungan jangka panjang, dan fokus pada keamanan. CentOS adalah versi _community-driven_ dari RHEL.
- **Fedora:** Distro yang didukung Red Hat, sering menjadi tempat pengujian fitur-fitur baru sebelum masuk ke RHEL. Cocok untuk pengguna yang ingin fitur terbaru.
- **Arch Linux:** Dikenal karena pendekatannya yang "rolling release" dan minimalis, memberikan pengguna kontrol penuh atas instalasi. Lebih cocok untuk pengguna berpengalaman.

### Mengapa Linux Penting dalam Networking dan Cybersecurity

Linux adalah tulang punggung internet dan infrastruktur modern. Berikut alasannya:

- **Stabilitas dan Keandalan:** Linux dikenal sangat stabil dan dapat berjalan berbulan-bulan atau bahkan bertahun-tahun tanpa perlu _reboot_. Ini krusial untuk server jaringan dan sistem cloud yang harus selalu aktif.
- **Keamanan:** Dengan model _open-source_ dan komunitas yang aktif, celah keamanan seringkali ditemukan dan diperbaiki dengan cepat. Linux juga menawarkan kontrol granular atas izin file dan proses, yang penting untuk mengamankan sistem. Banyak alat _cybersecurity_ (misalnya, Nmap, Wireshark, Metasploit) dikembangkan untuk dan berjalan optimal di Linux.
- **Fleksibilitas dan Kustomisasi:** Linux dapat disesuaikan untuk berbagai kebutuhan, mulai dari server web ringan hingga superkomputer. Ini memungkinkan administrator jaringan dan profesional keamanan untuk membangun sistem yang sangat spesifik dan efisien.
- **Dukungan Jaringan Bawaan:** Linux memiliki dukungan jaringan yang sangat kuat dan terintegrasi, menjadikannya pilihan utama untuk _router_, _firewall_, server DNS, dan berbagai layanan jaringan lainnya.
- **Efisiensi Sumber Daya:** Linux dapat berjalan dengan baik pada perangkat keras dengan sumber daya terbatas, menjadikannya ideal untuk perangkat IoT, server kecil, atau mesin virtual di cloud.
- **Alat Baris Perintah yang Kuat:** Sebagian besar konfigurasi dan administrasi di Linux dilakukan melalui baris perintah, yang sangat efisien untuk otomatisasi dan manajemen jarak jauh, keterampilan penting dalam networking dan cloud.

### Struktur Direktori Linux

Sistem file Linux mengikuti hierarki standar yang disebut _Filesystem Hierarchy Standard_ (FHS). Memahami struktur ini penting untuk navigasi dan administrasi sistem:

- `/` (Root): Direktori utama dari seluruh sistem file
- `/home`: Direktori home untuk pengguna biasa (misalnya `/home/siswa1`)
- `/root`: Direktori home untuk pengguna root (administrator)
- `/bin`: Berisi perintah-perintah dasar yang diperlukan untuk sistem (ls, cp, mv, dll)
- `/usr/bin`: Berisi perintah-perintah untuk pengguna
- `/sbin`: Berisi perintah-perintah administratif sistem
- `/etc`: Berisi file konfigurasi sistem
- `/var`: Berisi data yang berubah-ubah (log, cache, spool)
- `/tmp`: Direktori untuk file sementara
- `/proc`: Sistem file virtual yang berisi informasi tentang proses dan kernel
- `/sys`: Sistem file virtual yang berisi informasi tentang perangkat keras
- `/dev`: Berisi file perangkat (device files)
- `/lib`: Berisi library yang diperlukan oleh program di /bin dan /sbin
- `/usr`: Berisi program, library, dan data untuk pengguna
- `/opt`: Direktori untuk software tambahan
- `/mnt` dan `/media`: Titik mount untuk perangkat penyimpanan

## Perintah Dasar Linux

Menguasai perintah dasar Linux adalah kunci untuk berinteraksi dengan sistem.

### Navigasi Direktori

- `pwd` (Print Working Directory): Menampilkan lokasi direktori saat ini.
    
    ```bash
    pwd
    # Output: /home/user/documents
    ```
    
- `ls` (List): Menampilkan daftar file dan direktori di lokasi saat ini.
    
    - `ls -l`: Menampilkan detail (izin, pemilik, ukuran, tanggal).
    - `ls -a`: Menampilkan semua file, termasuk yang tersembunyi (diawali dengan `.`).
    - `ls -lh`: Menampilkan ukuran file dalam format yang mudah dibaca (Human-readable).
    - `ls -la`: Kombinasi menampilkan semua file dengan detail.
    - `ls -R`: Menampilkan isi direktori secara rekursif.
    
    ```bash
    ls
    # Output: file1.txt mydir anotherfile.jpg
    
    ls -l
    # Output:
    # -rw-r--r-- 1 user user 1024 Jul 27 10:00 file1.txt
    # drwxr-xr-x 2 user user 4096 Jul 27 10:05 mydir
    ```
    
- `cd` (Change Directory): Berpindah antar direktori.
    
    - `cd ..`: Pindah ke direktori induk.
    - `cd ~`: Pindah ke direktori home pengguna.
    - `cd /`: Pindah ke direktori root.
    - `cd /path/to/directory`: Pindah ke direktori spesifik.
    - `cd -`: Pindah ke direktori sebelumnya.
    
    ```bash
    cd mydir
    pwd
    # Output: /home/user/documents/mydir
    
    cd ..
    pwd
    # Output: /home/user/documents
    ```
    
- `tree`: Menampilkan struktur direktori dalam bentuk pohon (perlu diinstal: `sudo apt install tree`).
    
    ```bash
    tree
    # Output:
    # .
    # ├── file1.txt
    # ├── mydir
    # │   └── subfile.txt
    # └── anotherfile.jpg
    ```
    

### Manajemen File dan Direktori

- `mkdir` (Make Directory): Membuat direktori baru.
    
    - `mkdir -p path/to/nested/directories`: Membuat direktori bersarang sekaligus.
    
    ```bash
    mkdir new_folder
    mkdir -p project/src/main/java
    ```
    
- `rmdir` (Remove Directory): Menghapus direktori kosong.
    
    ```bash
    rmdir empty_folder
    ```
    
- `cp` (Copy): Menyalin file atau direktori.
    
    - `cp file.txt /path/to/destination/`: Menyalin file.
    - `cp -r folder /path/to/destination/`: Menyalin direktori secara rekursif.
    - `cp -i file.txt backup.txt`: Menyalin dengan konfirmasi jika file tujuan sudah ada.
    - `cp -u source dest`: Menyalin hanya jika file sumber lebih baru.
    
    ```bash
    cp file1.txt file1_copy.txt
    cp -r mydir backup_mydir
    ```
    
- `mv` (Move/Rename): Memindahkan atau mengganti nama file/direktori.
    
    ```bash
    mv file1.txt new_name.txt
    mv new_name.txt /path/to/another/folder/
    ```
    
- `rm` (Remove): Menghapus file atau direktori.
    
    - `rm file.txt`: Menghapus file.
    - `rm -r folder`: Menghapus direktori dan isinya secara rekursif.
    - `rm -rf folder`: Menghapus direktori dan isinya secara paksa (hati-hati!).
    - `rm -i file.txt`: Menghapus dengan konfirmasi.
    
    ```bash
    rm old_file.txt
    rm -r backup_mydir
    ```
    
- `touch`: Membuat file kosong baru atau memperbarui timestamp file yang sudah ada.
    
    ```bash
    touch new_empty_file.txt
    touch -t 202307271200 file.txt  # Set waktu spesifik
    ```
    
- `ln` (Link): Membuat link ke file atau direktori.
    
    - `ln -s target linkname`: Membuat symbolic link (shortcut).
    - `ln target linkname`: Membuat hard link.
    
    ```bash
    ln -s /path/to/original/file.txt shortcut.txt
    ```
    
- `find`: Mencari file dan direktori berdasarkan kriteria.
    
    ```bash
    find /home -name "*.txt"           # Cari file .txt di /home
    find . -type d -name "project*"    # Cari direktori yang dimulai dengan "project"
    find . -size +100M                 # Cari file lebih besar dari 100MB
    find . -mtime -7                   # Cari file yang dimodifikasi dalam 7 hari terakhir
    ```
    
- `locate`: Mencari file dengan cepat menggunakan database (perlu `updatedb` untuk memperbarui).
    
    ```bash
    locate filename.txt
    sudo updatedb  # Perbarui database locate
    ```
    

### Melihat Isi File

- `cat` (Concatenate): Menampilkan seluruh isi file ke standar output.
    
    - `cat file1.txt file2.txt`: Menggabungkan dan menampilkan beberapa file.
    
    ```bash
    cat mydocument.txt
    ```
    
- `less`: Menampilkan isi file satu layar penuh pada satu waktu, memungkinkan _scrolling_ maju dan mundur. Tekan `q` untuk keluar.
    
    ```bash
    less large_log_file.log
    ```
    
- `more`: Mirip dengan `less`, tetapi hanya memungkinkan _scrolling_ maju. Tekan `Space` untuk halaman berikutnya, `q` untuk keluar.
    
    ```bash
    more another_large_file.txt
    ```
    
- `head`: Menampilkan beberapa baris pertama dari file (default: 10 baris).
    
    - `head -n 5 file.txt`: Menampilkan 5 baris pertama.
    
    ```bash
    head mydocument.txt
    ```
    
- `tail`: Menampilkan beberapa baris terakhir dari file (default: 10 baris). Berguna untuk melihat log yang sedang diperbarui.
    
    - `tail -n 5 file.txt`: Menampilkan 5 baris terakhir.
    - `tail -f logfile.log`: Mengikuti (follow) perubahan pada file log secara _real-time_.
    
    ```bash
    tail access.log
    ```
    
- `grep` (Global Regular Expression Print): Mencari pola teks dalam file.
    
    ```bash
    grep "error" logfile.txt           # Cari kata "error"
    grep -i "Error" logfile.txt        # Cari tanpa memperhatikan case
    grep -n "error" logfile.txt        # Tampilkan nomor baris
    grep -r "function" /path/to/code/  # Cari secara rekursif dalam direktori
    grep -v "debug" logfile.txt        # Tampilkan baris yang TIDAK mengandung "debug"
    ```
    
- `wc` (Word Count): Menghitung baris, kata, dan karakter dalam file.
    
    ```bash
    wc file.txt           # Tampilkan baris, kata, karakter
    wc -l file.txt        # Hitung baris saja
    wc -w file.txt        # Hitung kata saja
    ```
    
- `sort`: Mengurutkan isi file.
    
    ```bash
    sort names.txt        # Urutkan secara alfabetis
    sort -n numbers.txt   # Urutkan secara numerik
    sort -r file.txt      # Urutkan terbalik
    ```
    
- `uniq`: Menghapus baris duplikat yang berurutan.
    
    ```bash
    sort names.txt | uniq    # Hapus duplikat setelah diurutkan
    uniq -c file.txt         # Hitung kemunculan setiap baris
    ```
    

### Manajemen Izin File

Sistem izin file Linux sangat penting untuk keamanan. Setiap file dan direktori memiliki izin untuk tiga kategori: pemilik (owner), grup (group), dan lainnya (others). Izin ini adalah:

- `r` (read): Membaca isi file atau melihat isi direktori.
- `w` (write): Mengubah isi file atau membuat/menghapus file di direktori.
- `x` (execute): Menjalankan file (jika itu program/script) atau masuk ke direktori.

Izin direpresentasikan dalam format simbolik (misalnya, `rwxr-xr-x`) atau numerik (oktal).

- `chmod` (Change Mode): Mengubah izin file atau direktori.
    
    - **Simbolik:**
        
        - `u`: user (pemilik), `g`: group, `o`: others, `a`: all.
        - `+`: menambah izin, `-`: menghapus izin, `=`: mengatur izin secara spesifik.
        
        ```bash
        chmod u+x myscript.sh      # Menambah izin eksekusi untuk pemilik
        chmod go-w myfile.txt      # Menghapus izin tulis untuk grup dan lainnya
        chmod a=rw- mydata.txt     # Mengatur izin baca/tulis untuk semua
        ```
        
    - **Numerik (Oktal):** Setiap izin (r, w, x) memiliki nilai numerik: `r=4`, `w=2`, `x=1`. Jumlahkan nilai-nilai ini untuk setiap kategori.
        
        - `7 (rwx)`: Baca, Tulis, Eksekusi
        - `6 (rw-)`: Baca, Tulis
        - `5 (r-x)`: Baca, Eksekusi
        - `4 (r--)`: Baca
        
        ```bash
        chmod 755 myscript.sh      # Pemilik: rwx, Grup: r-x, Lainnya: r-x
        chmod 644 myfile.txt       # Pemilik: rw-, Grup: r--, Lainnya: r--
        chmod 600 secret.txt       # Hanya pemilik yang bisa baca/tulis
        ```
        
- `chown` (Change Owner): Mengubah pemilik file atau direktori.
    
    ```bash
    sudo chown newuser file.txt
    sudo chown newuser:newgroup folder/    # Mengubah pemilik dan grup
    sudo chown -R user:group directory/    # Ubah secara rekursif
    ```
    
- `chgrp` (Change Group): Mengubah grup pemilik file atau direktori.
    
    ```bash
    sudo chgrp developers project/
    ```
    
- `umask`: Mengatur izin default untuk file dan direktori yang baru dibuat.
    
    ```bash
    umask 022    # File baru: 644, Direktori baru: 755
    umask        # Lihat setting umask saat ini
    ```
    

## Manajemen Proses

Memahami dan mengelola proses adalah keterampilan penting dalam administrasi Linux.

### Melihat Proses yang Berjalan

- `ps` (Process Status): Menampilkan proses yang sedang berjalan.
    
    ```bash
    ps               # Proses milik pengguna saat ini
    ps aux           # Semua proses dengan detail lengkap
    ps -ef           # Format berbeda untuk semua proses
    ps -u username   # Proses milik pengguna tertentu
    ```
    
- `top`: Menampilkan proses secara real-time dengan penggunaan CPU dan memori.
    
    ```bash
    top
    # Tekan 'q' untuk keluar, 'k' untuk kill proses
    ```
    
- `htop`: Versi yang lebih interaktif dari `top` (perlu diinstal).
    
    ```bash
    sudo apt install htop
    htop
    ```
    
- `pgrep`: Mencari proses berdasarkan nama.
    
    ```bash
    pgrep firefox      # Cari PID proses firefox
    pgrep -u user      # Cari proses milik user tertentu
    ```
    

### Mengelola Proses

- `kill`: Menghentikan proses berdasarkan PID.
    
    ```bash
    kill 1234          # Hentikan proses dengan PID 1234
    kill -9 1234       # Paksa stop proses (SIGKILL)
    kill -15 1234      # Stop proses dengan normal (SIGTERM)
    ```
    
- `killall`: Menghentikan proses berdasarkan nama.
    
    ```bash
    killall firefox    # Hentikan semua proses firefox
    killall -9 chrome  # Paksa stop semua proses chrome
    ```
    
- `pkill`: Menghentikan proses berdasarkan pola nama.
    
    ```bash
    pkill -f "python script.py"    # Hentikan proses berdasarkan command line
    ```
    
- `jobs`: Melihat job yang berjalan di background.
    
    ```bash
    jobs               # Lihat job aktif
    ```
    
- `bg` dan `fg`: Memindahkan job antara background dan foreground.
    
    ```bash
    command &          # Jalankan di background
    bg %1              # Pindahkan job 1 ke background
    fg %1              # Pindahkan job 1 ke foreground
    ```
    
- `nohup`: Menjalankan perintah yang tidak akan terhenti saat terminal ditutup.
    
    ```bash
    nohup long-running-command &
    ```
    

## Manajemen Pengguna dan Grup

Mengelola pengguna dan grup adalah tugas dasar administrasi sistem Linux.

- `useradd`: Membuat pengguna baru.
    
    ```bash
    sudo useradd -m siswa1               # Buat user dengan home directory
    sudo useradd -m -s /bin/bash siswa2  # Buat user dengan shell bash
    sudo useradd -m -G sudo siswa3       # Buat user dan tambahkan ke grup sudo
    ```
    
- `passwd`: Mengatur atau mengubah kata sandi pengguna.
    
    ```bash
    sudo passwd siswa1    # Set password untuk siswa1
    passwd                # Ubah password sendiri
    ```
    
- `userdel`: Menghapus pengguna.
    
    ```bash
    sudo userdel siswa1      # Hapus user saja
    sudo userdel -r siswa1   # Hapus user dan home directory
    ```
    
- `groupadd`: Membuat grup baru.
    
    ```bash
    sudo groupadd network_admins
    sudo groupadd developers
    ```
    
- `groupdel`: Menghapus grup.
    
    ```bash
    sudo groupdel network_admins
    ```
    
- `usermod`: Memodifikasi properti pengguna.
    
    ```bash
    sudo usermod -aG sudo siswa1         # Tambahkan ke grup sudo
    sudo usermod -aG developers siswa1   # Tambahkan ke grup developers
    sudo usermod -s /bin/zsh siswa1      # Ubah shell default
    sudo usermod -l newname oldname      # Ubah nama login
    ```
    
- `id`: Menampilkan informasi pengguna dan grup.
    
    ```bash
    id siswa1        # Info lengkap tentang siswa1
    id -u siswa1     # UID saja
    id -g siswa1     # GID saja
    ```
    
- `who` dan `w`: Melihat pengguna yang sedang login.
    
    ```bash
    who              # Pengguna yang login
    w                # Info lebih detail termasuk aktivitas
    ```
    
- `su` dan `sudo`: Beralih pengguna atau menjalankan perintah sebagai pengguna lain.
    
    ```bash
    su - siswa1      # Beralih ke siswa1
    sudo command     # Jalankan command sebagai root
    sudo -u siswa1 command  # Jalankan command sebagai siswa1
    ```
    
- `groups`: Melihat grup yang dimiliki pengguna.
    
    ```bash
    groups           # Grup milik user saat ini
    groups siswa1    # Grup milik siswa1
    ```
    

## Manajemen Paket

Manajer paket adalah alat yang digunakan untuk menginstal, memperbarui, mengkonfigurasi, dan menghapus perangkat lunak di Linux.

### Pengenalan Manajer Paket

- **APT (Advanced Package Tool):** Digunakan pada distribusi berbasis Debian (Ubuntu, Debian, Mint).
- **YUM/DNF (Yellowdog Updater Modified / Dandified YUM):** Digunakan pada distribusi berbasis Red Hat (CentOS, Fedora, RHEL). DNF adalah penerus YUM.
- **Pacman:** Digunakan pada Arch Linux dan turunannya.
- **Zypper:** Digunakan pada openSUSE.

### Instalasi, Pembaruan, dan Penghapusan Paket

**Untuk distribusi berbasis Debian (APT):**

- `sudo apt update`: Memperbarui daftar paket yang tersedia dari repositori.
    
    ```bash
    sudo apt update
    ```
    
- `sudo apt upgrade`: Memperbarui semua paket yang terinstal ke versi terbaru.
    
    ```bash
    sudo apt upgradesudo apt full-upgrade  # Upgrade yang lebih agresif
    ```
    
- `sudo apt install nama_paket`: Menginstal paket baru.
    
    ```bash
    sudo apt install net-tools     # Alat jaringansudo apt install vim git curl  # Install beberapa paket sekaligus
    ```
    
- `sudo apt remove nama_paket`: Menghapus paket, tetapi file konfigurasi mungkin tetap ada.
    
    ```bash
    sudo apt remove net-tools
    ```
    
- `sudo apt purge nama_paket`: Menghapus paket beserta file konfigurasinya.
    
    ```bash
    sudo apt purge net-tools
    ```
    
- `sudo apt autoremove`: Menghapus paket-paket yang tidak lagi diperlukan.
    
    ```bash
    sudo apt autoremove
    ```
    
- `apt search keyword`: Mencari paket berdasarkan kata kunci.
    
    ```bash
    apt search editor
    ```
    
- `apt show nama_paket`: Menampilkan informasi detail tentang paket.
    
    ```bash
    apt show vim
    ```
    
- `apt list --installed`: Menampilkan semua paket yang terinstal.
    
    ```bash
    apt list --installed | grep vim
    ```
    

**Untuk distribusi berbasis Red Hat (YUM/DNF):**

- `sudo dnf check-update`: Memeriksa pembaruan yang tersedia.
- `sudo dnf update`: Memperbarui semua paket yang terinstal.
- `sudo dnf install nama_paket`: Menginstal paket baru.
- `sudo dnf remove nama_paket`: Menghapus paket.
- `dnf search keyword`: Mencari paket.
- `dnf info nama_paket`: Info detail paket.

### Manajemen Repository

- **Menambah repository (Ubuntu/Debian):**
    
    ```bash
    sudo add-apt-repository ppa:repository-name
    sudo apt update
    ```
    
- **Melihat repository yang aktif:**
    
    ```bash
    cat /etc/apt/sources.list
    ls /etc/apt/sources.list.d/
    ```
    

### Instalasi dari Source dan Package Manager Alternatif

- **Snap packages:**
    
    ```bash
    sudo snap install package-name
    sudo snap list
    sudo snap remove package-name
    ```
    
- **Flatpak:**
    
    ```bash
    sudo apt install flatpak
    flatpak install flathub com.application.name
    ```
    

## Sistem File dan Mount

### Melihat Informasi Disk dan Partisi

- `df`: Menampilkan penggunaan disk.
    
    ```bash
    df -h            # Human readable format
    df -i            # Info inode
    ```
    
- `du`: Menampilkan ukuran direktori.
    
    ```bash
    du -h /home      # Ukuran direktori /home
    du -sh *         # Ukuran semua item di direktori saat ini
    du -ah /var/log  # Ukuran semua file termasuk hidden
    ```
    
- `lsblk`: Menampilkan block devices dalam format tree.
    
    ```bash
    lsblk
    ```
    
- `fdisk`: Mengelola partisi disk.
    
    ```bash
    sudo fdisk -l    # List semua disk dan partisi
    ```
    

### Mount dan Unmount

- `mount`: Memasang filesystem.
    
    ```bash
    sudo mount /dev/sdb1 /mnt/usb         # Mount USB drive
    sudo mount -t ntfs /dev/sdb1 /mnt/windows  # Mount dengan filesystem type
    ```
    
- `umount`: Melepas filesystem.
    
    ```bash
    sudo umount /mnt/usb
    ```
    
- Konfigurasi automount di `/etc/fstab`:
    
    ```bash
    sudo nano /etc/fstab
    # Tambahkan baris seperti:
    # /dev/sdb1 /mnt/data ext4 defaults 0 2
    ```
    

## Jaringan di Linux

### Perintah Dasar Jaringan

- `ping`: Menguji konektivitas jaringan.
    
    ```bash
    ping google.com
    ping -c 4 8.8.8.8      # Ping 4 kali saja
    ping6 ipv6.google.com  # Ping menggunakan IPv6
    ```
    
- `wget` dan `curl`: Download file dari internet.
    
    ```bash
    wget https://example.com/file.zip
    curl -O https://example.com/file.zip    # Download dengan nama asli
    curl -L https://example.com/redirected  # Follow redirect
    ```
    
- `ssh`: Koneksi remote yang aman.
    
    ```bash
    ssh user@server.com
    ssh -p 2222 user@server.com  # Koneksi ke port khusus
    ```
    
- `scp`: Copy file melalui SSH.
    
    ```bash
    scp file.txt user@server:/remote/path/
    scp -r folder user@server:/remote/path/  # Copy direktori
    ```
    
- `rsync`: Sinkronisasi file yang efisien.
    
    ```bash
    rsync -avz /local/path/ user@server:/remote/path/
    ```
    

### Konfigurasi Jaringan

- `ip`: Perintah modern untuk konfigurasi jaringan.
    
    ```bash
    ip addr show        # Tampilkan alamat IP
    ip route show       # Tampilkan routing table
    ip link show        # Tampilkan network interfaces
    ```
    
- `ifconfig`: Perintah lama untuk konfigurasi interface (perlu net-tools).
    
    ```bash
    ifconfig            # Tampilkan semua interface
    ifconfig eth0       # Info interface tertentu
    ```
    
- `netstat`: Tampilkan koneksi jaringan.
    
    ```bash
    netstat -tuln       # TCP dan UDP listening ports
    netstat -r          # Routing table
    ```
    
- `ss`: Pengganti modern netstat.
    
    ```bash
    ss -tuln           # Listening ports
    ss -t -a           # Semua TCP connections
    ```
    

## Monitoring Sistem

### Monitoring Resource

- `free`: Menampilkan penggunaan memori.
    
    ```bash
    free -h            # Human readable
    free -s 2          # Update setiap 2 detik
    ```
    
- `uptime`: Menampilkan uptime dan load average.
    
    ```bash
    uptime
    ```
    
- `vmstat`: Statistik virtual memory.
    
    ```bash
    vmstat 2 5         # Update setiap 2 detik, 5 kali
    ```
    
- `iostat`: Statistik I/O (perlu sysstat package).
    
    ```bash
    sudo apt install sysstat
    iostat -x 2        # Extended info, update setiap 2 detik
    ```
    

### Log System

: Pindah ke akhir baris. * `G`: Pindah ke akhir file. * `gg`: Pindah ke awal file. * `Ctrl + f`: Page down. * `Ctrl + b`: Page up. * **Menghapus (di Mode Normal):** * `x`: Menghapus karakter di bawah kursor. * `dd`: Menghapus seluruh baris. * `dw`: Menghapus kata. * `d# Modul 1: Dasar-dasar Linux

## Pengenalan Linux

### Apa itu Linux? Sejarah Singkat dan Filosofi

Linux adalah sistem operasi _open-source_ berbasis kernel Linux. Kernel ini pertama kali dirilis oleh Linus Torvalds pada tahun 1991. Berbeda dengan sistem operasi komersial seperti Windows atau macOS, Linux dikembangkan secara kolaboratif oleh komunitas global dan didistribusikan di bawah lisensi _General Public License_ (GPL), yang berarti siapa pun bebas menggunakan, memodifikasi, dan mendistribusikannya.

Filosofi utama Linux adalah kebebasan dan keterbukaan. Ini mendorong inovasi, transparansi, dan kemampuan bagi pengguna untuk mengontrol penuh sistem mereka.

### Distribusi Linux Populer

Linux hadir dalam berbagai "distribusi" (sering disebut "distro"), yang merupakan bundel kernel Linux dengan perangkat lunak sistem, pustaka, alat, dan lingkungan desktop. Beberapa distro populer meliputi:

- **Ubuntu:** Sangat populer untuk pemula dan penggunaan desktop, juga banyak digunakan di server dan cloud. Dikenal karena kemudahan penggunaan dan komunitas yang besar.
- **Debian:** Fondasi bagi banyak distro lain (termasuk Ubuntu). Dikenal karena stabilitas dan keamanannya.
- **CentOS/Red Hat Enterprise Linux (RHEL):** Sangat populer di lingkungan server dan perusahaan karena stabilitas, dukungan jangka panjang, dan fokus pada keamanan. CentOS adalah versi _community-driven_ dari RHEL.
- **Fedora:** Distro yang didukung Red Hat, sering menjadi tempat pengujian fitur-fitur baru sebelum masuk ke RHEL. Cocok untuk pengguna yang ingin fitur terbaru.
- **Arch Linux:** Dikenal karena pendekatannya yang "rolling release" dan minimalis, memberikan pengguna kontrol penuh atas instalasi. Lebih cocok untuk pengguna berpengalaman.

### Mengapa Linux Penting dalam Networking dan Cybersecurity

Linux adalah tulang punggung internet dan infrastruktur modern. Berikut alasannya:

- **Stabilitas dan Keandalan:** Linux dikenal sangat stabil dan dapat berjalan berbulan-bulan atau bahkan bertahun-tahun tanpa perlu _reboot_. Ini krusial untuk server jaringan dan sistem cloud yang harus selalu aktif.
- **Keamanan:** Dengan model _open-source_ dan komunitas yang aktif, celah keamanan seringkali ditemukan dan diperbaiki dengan cepat. Linux juga menawarkan kontrol granular atas izin file dan proses, yang penting untuk mengamankan sistem. Banyak alat _cybersecurity_ (misalnya, Nmap, Wireshark, Metasploit) dikembangkan untuk dan berjalan optimal di Linux.
- **Fleksibilitas dan Kustomisasi:** Linux dapat disesuaikan untuk berbagai kebutuhan, mulai dari server web ringan hingga superkomputer. Ini memungkinkan administrator jaringan dan profesional keamanan untuk membangun sistem yang sangat spesifik dan efisien.
- **Dukungan Jaringan Bawaan:** Linux memiliki dukungan jaringan yang sangat kuat dan terintegrasi, menjadikannya pilihan utama untuk _router_, _firewall_, server DNS, dan berbagai layanan jaringan lainnya.
- **Efisiensi Sumber Daya:** Linux dapat berjalan dengan baik pada perangkat keras dengan sumber daya terbatas, menjadikannya ideal untuk perangkat IoT, server kecil, atau mesin virtual di cloud.
- **Alat Baris Perintah yang Kuat:** Sebagian besar konfigurasi dan administrasi di Linux dilakukan melalui baris perintah, yang sangat efisien untuk otomatisasi dan manajemen jarak jauh, keterampilan penting dalam networking dan cloud.

### Struktur Direktori Linux

Sistem file Linux mengikuti hierarki standar yang disebut _Filesystem Hierarchy Standard_ (FHS). Memahami struktur ini penting untuk navigasi dan administrasi sistem:

- `/` (Root): Direktori utama dari seluruh sistem file
- `/home`: Direktori home untuk pengguna biasa (misalnya `/home/siswa1`)
- `/root`: Direktori home untuk pengguna root (administrator)
- `/bin`: Berisi perintah-perintah dasar yang diperlukan untuk sistem (ls, cp, mv, dll)
- `/usr/bin`: Berisi perintah-perintah untuk pengguna
- `/sbin`: Berisi perintah-perintah administratif sistem
- `/etc`: Berisi file konfigurasi sistem
- `/var`: Berisi data yang berubah-ubah (log, cache, spool)
- `/tmp`: Direktori untuk file sementara
- `/proc`: Sistem file virtual yang berisi informasi tentang proses dan kernel
- `/sys`: Sistem file virtual yang berisi informasi tentang perangkat keras
- `/dev`: Berisi file perangkat (device files)
- `/lib`: Berisi library yang diperlukan oleh program di /bin dan /sbin
- `/usr`: Berisi program, library, dan data untuk pengguna
- `/opt`: Direktori untuk software tambahan
- `/mnt` dan `/media`: Titik mount untuk perangkat penyimpanan

## Perintah Dasar Linux

Menguasai perintah dasar Linux adalah kunci untuk berinteraksi dengan sistem.

### Navigasi Direktori

- `pwd` (Print Working Directory): Menampilkan lokasi direktori saat ini.
    
    ```bash
    pwd
    # Output: /home/user/documents
    ```
    
- `ls` (List): Menampilkan daftar file dan direktori di lokasi saat ini.
    
    - `ls -l`: Menampilkan detail (izin, pemilik, ukuran, tanggal).
    - `ls -a`: Menampilkan semua file, termasuk yang tersembunyi (diawali dengan `.`).
    - `ls -lh`: Menampilkan ukuran file dalam format yang mudah dibaca (Human-readable).
    - `ls -la`: Kombinasi menampilkan semua file dengan detail.
    - `ls -R`: Menampilkan isi direktori secara rekursif.
    
    ```bash
    ls
    # Output: file1.txt mydir anotherfile.jpg
    
    ls -l
    # Output:
    # -rw-r--r-- 1 user user 1024 Jul 27 10:00 file1.txt
    # drwxr-xr-x 2 user user 4096 Jul 27 10:05 mydir
    ```
    
- `cd` (Change Directory): Berpindah antar direktori.
    
    - `cd ..`: Pindah ke direktori induk.
    - `cd ~`: Pindah ke direktori home pengguna.
    - `cd /`: Pindah ke direktori root.
    - `cd /path/to/directory`: Pindah ke direktori spesifik.
    - `cd -`: Pindah ke direktori sebelumnya.
    
    ```bash
    cd mydir
    pwd
    # Output: /home/user/documents/mydir
    
    cd ..
    pwd
    # Output: /home/user/documents
    ```
    
- `tree`: Menampilkan struktur direktori dalam bentuk pohon (perlu diinstal: `sudo apt install tree`).
    
    ```bash
    tree
    # Output:
    # .
    # ├── file1.txt
    # ├── mydir
    # │   └── subfile.txt
    # └── anotherfile.jpg
    ```
    

### Manajemen File dan Direktori

- `mkdir` (Make Directory): Membuat direktori baru.
    
    - `mkdir -p path/to/nested/directories`: Membuat direktori bersarang sekaligus.
    
    ```bash
    mkdir new_folder
    mkdir -p project/src/main/java
    ```
    
- `rmdir` (Remove Directory): Menghapus direktori kosong.
    
    ```bash
    rmdir empty_folder
    ```
    
- `cp` (Copy): Menyalin file atau direktori.
    
    - `cp file.txt /path/to/destination/`: Menyalin file.
    - `cp -r folder /path/to/destination/`: Menyalin direktori secara rekursif.
    - `cp -i file.txt backup.txt`: Menyalin dengan konfirmasi jika file tujuan sudah ada.
    - `cp -u source dest`: Menyalin hanya jika file sumber lebih baru.
    
    ```bash
    cp file1.txt file1_copy.txt
    cp -r mydir backup_mydir
    ```
    
- `mv` (Move/Rename): Memindahkan atau mengganti nama file/direktori.
    
    ```bash
    mv file1.txt new_name.txt
    mv new_name.txt /path/to/another/folder/
    ```
    
- `rm` (Remove): Menghapus file atau direktori.
    
    - `rm file.txt`: Menghapus file.
    - `rm -r folder`: Menghapus direktori dan isinya secara rekursif.
    - `rm -rf folder`: Menghapus direktori dan isinya secara paksa (hati-hati!).
    - `rm -i file.txt`: Menghapus dengan konfirmasi.
    
    ```bash
    rm old_file.txt
    rm -r backup_mydir
    ```
    
- `touch`: Membuat file kosong baru atau memperbarui timestamp file yang sudah ada.
    
    ```bash
    touch new_empty_file.txt
    touch -t 202307271200 file.txt  # Set waktu spesifik
    ```
    
- `ln` (Link): Membuat link ke file atau direktori.
    
    - `ln -s target linkname`: Membuat symbolic link (shortcut).
    - `ln target linkname`: Membuat hard link.
    
    ```bash
    ln -s /path/to/original/file.txt shortcut.txt
    ```
    
- `find`: Mencari file dan direktori berdasarkan kriteria.
    
    ```bash
    find /home -name "*.txt"           # Cari file .txt di /home
    find . -type d -name "project*"    # Cari direktori yang dimulai dengan "project"
    find . -size +100M                 # Cari file lebih besar dari 100MB
    find . -mtime -7                   # Cari file yang dimodifikasi dalam 7 hari terakhir
    ```
    
- `locate`: Mencari file dengan cepat menggunakan database (perlu `updatedb` untuk memperbarui).
    
    ```bash
    locate filename.txt
    sudo updatedb  # Perbarui database locate
    ```
    

### Melihat Isi File

- `cat` (Concatenate): Menampilkan seluruh isi file ke standar output.
    
    - `cat file1.txt file2.txt`: Menggabungkan dan menampilkan beberapa file.
    
    ```bash
    cat mydocument.txt
    ```
    
- `less`: Menampilkan isi file satu layar penuh pada satu waktu, memungkinkan _scrolling_ maju dan mundur. Tekan `q` untuk keluar.
    
    ```bash
    less large_log_file.log
    ```
    
- `more`: Mirip dengan `less`, tetapi hanya memungkinkan _scrolling_ maju. Tekan `Space` untuk halaman berikutnya, `q` untuk keluar.
    
    ```bash
    more another_large_file.txt
    ```
    
- `head`: Menampilkan beberapa baris pertama dari file (default: 10 baris).
    
    - `head -n 5 file.txt`: Menampilkan 5 baris pertama.
    
    ```bash
    head mydocument.txt
    ```
    
- `tail`: Menampilkan beberapa baris terakhir dari file (default: 10 baris). Berguna untuk melihat log yang sedang diperbarui.
    
    - `tail -n 5 file.txt`: Menampilkan 5 baris terakhir.
    - `tail -f logfile.log`: Mengikuti (follow) perubahan pada file log secara _real-time_.
    
    ```bash
    tail access.log
    ```
    
- `grep` (Global Regular Expression Print): Mencari pola teks dalam file.
    
    ```bash
    grep "error" logfile.txt           # Cari kata "error"
    grep -i "Error" logfile.txt        # Cari tanpa memperhatikan case
    grep -n "error" logfile.txt        # Tampilkan nomor baris
    grep -r "function" /path/to/code/  # Cari secara rekursif dalam direktori
    grep -v "debug" logfile.txt        # Tampilkan baris yang TIDAK mengandung "debug"
    ```
    
- `wc` (Word Count): Menghitung baris, kata, dan karakter dalam file.
    
    ```bash
    wc file.txt           # Tampilkan baris, kata, karakter
    wc -l file.txt        # Hitung baris saja
    wc -w file.txt        # Hitung kata saja
    ```
    
- `sort`: Mengurutkan isi file.
    
    ```bash
    sort names.txt        # Urutkan secara alfabetis
    sort -n numbers.txt   # Urutkan secara numerik
    sort -r file.txt      # Urutkan terbalik
    ```
    
- `uniq`: Menghapus baris duplikat yang berurutan.
    
    ```bash
    sort names.txt | uniq    # Hapus duplikat setelah diurutkan
    uniq -c file.txt         # Hitung kemunculan setiap baris
    ```
    

### Manajemen Izin File

Sistem izin file Linux sangat penting untuk keamanan. Setiap file dan direktori memiliki izin untuk tiga kategori: pemilik (owner), grup (group), dan lainnya (others). Izin ini adalah:

- `r` (read): Membaca isi file atau melihat isi direktori.
- `w` (write): Mengubah isi file atau membuat/menghapus file di direktori.
- `x` (execute): Menjalankan file (jika itu program/script) atau masuk ke direktori.

Izin direpresentasikan dalam format simbolik (misalnya, `rwxr-xr-x`) atau numerik (oktal).

- `chmod` (Change Mode): Mengubah izin file atau direktori.
    
    - **Simbolik:**
        
        - `u`: user (pemilik), `g`: group, `o`: others, `a`: all.
        - `+`: menambah izin, `-`: menghapus izin, `=`: mengatur izin secara spesifik.
        
        ```bash
        chmod u+x myscript.sh      # Menambah izin eksekusi untuk pemilik
        chmod go-w myfile.txt      # Menghapus izin tulis untuk grup dan lainnya
        chmod a=rw- mydata.txt     # Mengatur izin baca/tulis untuk semua
        ```
        
    - **Numerik (Oktal):** Setiap izin (r, w, x) memiliki nilai numerik: `r=4`, `w=2`, `x=1`. Jumlahkan nilai-nilai ini untuk setiap kategori.
        
        - `7 (rwx)`: Baca, Tulis, Eksekusi
        - `6 (rw-)`: Baca, Tulis
        - `5 (r-x)`: Baca, Eksekusi
        - `4 (r--)`: Baca
        
        ```bash
        chmod 755 myscript.sh      # Pemilik: rwx, Grup: r-x, Lainnya: r-x
        chmod 644 myfile.txt       # Pemilik: rw-, Grup: r--, Lainnya: r--
        chmod 600 secret.txt       # Hanya pemilik yang bisa baca/tulis
        ```
        
- `chown` (Change Owner): Mengubah pemilik file atau direktori.
    
    ```bash
    sudo chown newuser file.txt
    sudo chown newuser:newgroup folder/    # Mengubah pemilik dan grup
    sudo chown -R user:group directory/    # Ubah secara rekursif
    ```
    
- `chgrp` (Change Group): Mengubah grup pemilik file atau direktori.
    
    ```bash
    sudo chgrp developers project/
    ```
    
- `umask`: Mengatur izin default untuk file dan direktori yang baru dibuat.
    
    ```bash
    umask 022    # File baru: 644, Direktori baru: 755
    umask        # Lihat setting umask saat ini
    ```
    

## Manajemen Proses

Memahami dan mengelola proses adalah keterampilan penting dalam administrasi Linux.

### Melihat Proses yang Berjalan

- `ps` (Process Status): Menampilkan proses yang sedang berjalan.
    
    ```bash
    ps               # Proses milik pengguna saat ini
    ps aux           # Semua proses dengan detail lengkap
    ps -ef           # Format berbeda untuk semua proses
    ps -u username   # Proses milik pengguna tertentu
    ```
    
- `top`: Menampilkan proses secara real-time dengan penggunaan CPU dan memori.
    
    ```bash
    top
    # Tekan 'q' untuk keluar, 'k' untuk kill proses
    ```
    
- `htop`: Versi yang lebih interaktif dari `top` (perlu diinstal).
    
    ```bash
    sudo apt install htop
    htop
    ```
    
- `pgrep`: Mencari proses berdasarkan nama.
    
    ```bash
    pgrep firefox      # Cari PID proses firefox
    pgrep -u user      # Cari proses milik user tertentu
    ```
    

### Mengelola Proses

- `kill`: Menghentikan proses berdasarkan PID.
    
    ```bash
    kill 1234          # Hentikan proses dengan PID 1234
    kill -9 1234       # Paksa stop proses (SIGKILL)
    kill -15 1234      # Stop proses dengan normal (SIGTERM)
    ```
    
- `killall`: Menghentikan proses berdasarkan nama.
    
    ```bash
    killall firefox    # Hentikan semua proses firefox
    killall -9 chrome  # Paksa stop semua proses chrome
    ```
    
- `pkill`: Menghentikan proses berdasarkan pola nama.
    
    ```bash
    pkill -f "python script.py"    # Hentikan proses berdasarkan command line
    ```
    
- `jobs`: Melihat job yang berjalan di background.
    
    ```bash
    jobs               # Lihat job aktif
    ```
    
- `bg` dan `fg`: Memindahkan job antara background dan foreground.
    
    ```bash
    command &          # Jalankan di background
    bg %1              # Pindahkan job 1 ke background
    fg %1              # Pindahkan job 1 ke foreground
    ```
    
- `nohup`: Menjalankan perintah yang tidak akan terhenti saat terminal ditutup.
    
    ```bash
    nohup long-running-command &
    ```
    

## Manajemen Pengguna dan Grup

Mengelola pengguna dan grup adalah tugas dasar administrasi sistem Linux.

- `useradd`: Membuat pengguna baru.
    
    ```bash
    sudo useradd -m siswa1               # Buat user dengan home directory
    sudo useradd -m -s /bin/bash siswa2  # Buat user dengan shell bash
    sudo useradd -m -G sudo siswa3       # Buat user dan tambahkan ke grup sudo
    ```
    
- `passwd`: Mengatur atau mengubah kata sandi pengguna.
    
    ```bash
    sudo passwd siswa1    # Set password untuk siswa1
    passwd                # Ubah password sendiri
    ```
    
- `userdel`: Menghapus pengguna.
    
    ```bash
    sudo userdel siswa1      # Hapus user saja
    sudo userdel -r siswa1   # Hapus user dan home directory
    ```
    
- `groupadd`: Membuat grup baru.
    
    ```bash
    sudo groupadd network_admins
    sudo groupadd developers
    ```
    
- `groupdel`: Menghapus grup.
    
    ```bash
    sudo groupdel network_admins
    ```
    
- `usermod`: Memodifikasi properti pengguna.
    
    ```bash
    sudo usermod -aG sudo siswa1         # Tambahkan ke grup sudo
    sudo usermod -aG developers siswa1   # Tambahkan ke grup developers
    sudo usermod -s /bin/zsh siswa1      # Ubah shell default
    sudo usermod -l newname oldname      # Ubah nama login
    ```
    
- `id`: Menampilkan informasi pengguna dan grup.
    
    ```bash
    id siswa1        # Info lengkap tentang siswa1
    id -u siswa1     # UID saja
    id -g siswa1     # GID saja
    ```
    
- `who` dan `w`: Melihat pengguna yang sedang login.
    
    ```bash
    who              # Pengguna yang login
    w                # Info lebih detail termasuk aktivitas
    ```
    
- `su` dan `sudo`: Beralih pengguna atau menjalankan perintah sebagai pengguna lain.
    
    ```bash
    su - siswa1      # Beralih ke siswa1
    sudo command     # Jalankan command sebagai root
    sudo -u siswa1 command  # Jalankan command sebagai siswa1
    ```
    
- `groups`: Melihat grup yang dimiliki pengguna.
    
    ```bash
    groups           # Grup milik user saat ini
    groups siswa1    # Grup milik siswa1
    ```
    

## Manajemen Paket

Manajer paket adalah alat yang digunakan untuk menginstal, memperbarui, mengkonfigurasi, dan menghapus perangkat lunak di Linux.

### Pengenalan Manajer Paket

- **APT (Advanced Package Tool):** Digunakan pada distribusi berbasis Debian (Ubuntu, Debian, Mint).
- **YUM/DNF (Yellowdog Updater Modified / Dandified YUM):** Digunakan pada distribusi berbasis Red Hat (CentOS, Fedora, RHEL). DNF adalah penerus YUM.
- **Pacman:** Digunakan pada Arch Linux dan turunannya.
- **Zypper:** Digunakan pada openSUSE.

### Instalasi, Pembaruan, dan Penghapusan Paket

**Untuk distribusi berbasis Debian (APT):**

- `sudo apt update`: Memperbarui daftar paket yang tersedia dari repositori.
    
    ```bash
    sudo apt update
    ```
    
- `sudo apt upgrade`: Memperbarui semua paket yang terinstal ke versi terbaru.
    
    ```bash
    sudo apt upgradesudo apt full-upgrade  # Upgrade yang lebih agresif
    ```
    
- `sudo apt install nama_paket`: Menginstal paket baru.
    
    ```bash
    sudo apt install net-tools     # Alat jaringansudo apt install vim git curl  # Install beberapa paket sekaligus
    ```
    
- `sudo apt remove nama_paket`: Menghapus paket, tetapi file konfigurasi mungkin tetap ada.
    
    ```bash
    sudo apt remove net-tools
    ```
    
- `sudo apt purge nama_paket`: Menghapus paket beserta file konfigurasinya.
    
    ```bash
    sudo apt purge net-tools
    ```
    
- `sudo apt autoremove`: Menghapus paket-paket yang tidak lagi diperlukan.
    
    ```bash
    sudo apt autoremove
    ```
    
- `apt search keyword`: Mencari paket berdasarkan kata kunci.
    
    ```bash
    apt search editor
    ```
    
- `apt show nama_paket`: Menampilkan informasi detail tentang paket.
    
    ```bash
    apt show vim
    ```
    
- `apt list --installed`: Menampilkan semua paket yang terinstal.
    
    ```bash
    apt list --installed | grep vim
    ```
    

**Untuk distribusi berbasis Red Hat (YUM/DNF):**

- `sudo dnf check-update`: Memeriksa pembaruan yang tersedia.
- `sudo dnf update`: Memperbarui semua paket yang terinstal.
- `sudo dnf install nama_paket`: Menginstal paket baru.
- `sudo dnf remove nama_paket`: Menghapus paket.
- `dnf search keyword`: Mencari paket.
- `dnf info nama_paket`: Info detail paket.

### Manajemen Repository

- **Menambah repository (Ubuntu/Debian):**
    
    ```bash
    sudo add-apt-repository ppa:repository-name
    sudo apt update
    ```
    
- **Melihat repository yang aktif:**
    
    ```bash
    cat /etc/apt/sources.list
    ls /etc/apt/sources.list.d/
    ```
    

### Instalasi dari Source dan Package Manager Alternatif

- **Snap packages:**
    
    ```bash
    sudo snap install package-name
    sudo snap list
    sudo snap remove package-name
    ```
    
- **Flatpak:**
    
    ```bash
    sudo apt install flatpak
    flatpak install flathub com.application.name
    ```
    

## Sistem File dan Mount

### Melihat Informasi Disk dan Partisi

- `df`: Menampilkan penggunaan disk.
    
    ```bash
    df -h            # Human readable format
    df -i            # Info inode
    ```
    
- `du`: Menampilkan ukuran direktori.
    
    ```bash
    du -h /home      # Ukuran direktori /home
    du -sh *         # Ukuran semua item di direktori saat ini
    du -ah /var/log  # Ukuran semua file termasuk hidden
    ```
    
- `lsblk`: Menampilkan block devices dalam format tree.
    
    ```bash
    lsblk
    ```
    
- `fdisk`: Mengelola partisi disk.
    
    ```bash
    sudo fdisk -l    # List semua disk dan partisi
    ```
    

### Mount dan Unmount

- `mount`: Memasang filesystem.
    
    ```bash
    sudo mount /dev/sdb1 /mnt/usb         # Mount USB drive
    sudo mount -t ntfs /dev/sdb1 /mnt/windows  # Mount dengan filesystem type
    ```
    
- `umount`: Melepas filesystem.
    
    ```bash
    sudo umount /mnt/usb
    ```
    
- Konfigurasi automount di `/etc/fstab`:
    
    ```bash
    sudo nano /etc/fstab
    # Tambahkan baris seperti:
    # /dev/sdb1 /mnt/data ext4 defaults 0 2
    ```
    

## Jaringan di Linux

### Perintah Dasar Jaringan

- `ping`: Menguji konektivitas jaringan.
    
    ```bash
    ping google.com
    ping -c 4 8.8.8.8      # Ping 4 kali saja
    ping6 ipv6.google.com  # Ping menggunakan IPv6
    ```
    
- `wget` dan `curl`: Download file dari internet.
    
    ```bash
    wget https://example.com/file.zip
    curl -O https://example.com/file.zip    # Download dengan nama asli
    curl -L https://example.com/redirected  # Follow redirect
    ```
    
- `ssh`: Koneksi remote yang aman.
    
    ```bash
    ssh user@server.com
    ssh -p 2222 user@server.com  # Koneksi ke port khusus
    ```
    
- `scp`: Copy file melalui SSH.
    
    ```bash
    scp file.txt user@server:/remote/path/
    scp -r folder user@server:/remote/path/  # Copy direktori
    ```
    
- `rsync`: Sinkronisasi file yang efisien.
    
    ```bash
    rsync -avz /local/path/ user@server:/remote/path/
    ```
    

### Konfigurasi Jaringan

- `ip`: Perintah modern untuk konfigurasi jaringan.
    
    ```bash
    ip addr show        # Tampilkan alamat IP
    ip route show       # Tampilkan routing table
    ip link show        # Tampilkan network interfaces
    ```
    
- `ifconfig`: Perintah lama untuk konfigurasi interface (perlu net-tools).
    
    ```bash
    ifconfig            # Tampilkan semua interface
    ifconfig eth0       # Info interface tertentu
    ```
    
- `netstat`: Tampilkan koneksi jaringan.
    
    ```bash
    netstat -tuln       # TCP dan UDP listening ports
    netstat -r          # Routing table
    ```
    
- `ss`: Pengganti modern netstat.
    
    ```bash
    ss -tuln           # Listening ports
    ss -t -a           # Semua TCP connections
    ```
    

## Monitoring Sistem

### Monitoring Resource

- `free`: Menampilkan penggunaan memori.
    
    ```bash
    free -h            # Human readable
    free -s 2          # Update setiap 2 detik
    ```
    
- `uptime`: Menampilkan uptime dan load average.
    
    ```bash
    uptime
    ```
    
- `vmstat`: Statistik virtual memory.
    
    ```bash
    vmstat 2 5         # Update setiap 2 detik, 5 kali
    ```
    
- `iostat`: Statistik I/O (perlu sysstat package).
    
    ```bash
    sudo apt install sysstat
    iostat -x 2        # Extended info, update setiap 2 detik
    ```
    

### Log System

: Menghapus dari kursor hingga akhir baris. * **Copy dan Paste:** * `yy`: Copy baris. * `yw`: Copy kata. * `p`: Paste setelah kursor. * `P`: Paste sebelum kursor. * **Search dan Replace:** * `/pattern`: Cari pattern ke depan. * `?pattern`: Cari pattern ke belakang. * `n`: Cari berikutnya. * `N`: Cari sebelumnya. * `:%s/old/new/g`: Replace semua 'old' dengan 'new'.

### Konfigurasi Vim

Vim dapat dikustomisasi melalui file `~/.vimrc`:

```bash
nano ~/.vimrc
```

Contoh konfigurasi dasar:

```vim
" Enable syntax highlighting
syntax on

" Show line numbers
set number

" Enable auto-indentation
set autoindent
set smartindent

" Set tab width
set tabstop=4
set shiftwidth=4
set expandtab

" Enable search highlighting
set hlsearch
set incsearch

" Show matching brackets
set showmatch

" Enable mouse support
set mouse=a
```

## Dasar-dasar Shell Scripting

Shell scripting adalah cara untuk mengotomatisasi tugas-tugas di Linux dengan menulis serangkaian perintah dalam sebuah file.

### Konsep Dasar Scripting

- **Shebang:** Baris pertama dari setiap script shell harus dimulai dengan `#!` (disebut shebang), diikuti dengan path interpreter yang akan menjalankan script tersebut.
    
    ```bash
    #!/bin/bash
    #!/bin/sh
    #!/usr/bin/env python3
    ```
    
- **Komentar:** Baris yang dimulai dengan `#` adalah komentar dan diabaikan oleh interpreter.
    
    ```bash
    # Ini adalah komentar
    echo "Hello World"  # Komentar di akhir baris
    ```
    
- **Variabel:** Menyimpan nilai. Tidak ada spasi di sekitar tanda `=`.
    
    ```bash
    NAMA="Dunia"
    ANGKA=42
    PATH_FILE="/home/user/data.txt"
    echo "Halo, $NAMA!"
    echo "Angka: ${ANGKA}"
    ```
    
- **Variabel Lingkungan:**
    
    ```bash
    echo $HOME      # Direktori home
    echo $USER      # Nama pengguna
    echo $PATH      # Path executable
    echo $PWD       # Direktori saat ini
    ```
    
- **Input Pengguna:** Menggunakan perintah `read`.
    
    ```bash
    read -p "Masukkan nama Anda: " NAMA_PENGGUNA
    read -s -p "Masukkan password: " PASSWORD  # Input tersembunyi
    echo "Halo, $NAMA_PENGGUNA!"
    ```
    
- **Parameter Script:** Mengakses argumen yang diberikan saat menjalankan script.
    
    ```bash
    echo "Nama script: $0"
    echo "Parameter pertama: $1"
    echo "Parameter kedua: $2"
    echo "Semua parameter: $@"
    echo "Jumlah parameter: $#"
    ```
    

### Kontrol Alur

- **Kondisional (if-else):**
    
    ```bash
    if [ "$NAMA_PENGGUNA" == "Admin" ]; then
        echo "Selamat datang, Admin!"
    elif [ "$NAMA_PENGGUNA" == "Guest" ]; then
        echo "Halo, Guest!"
    else
        echo "Pengguna tidak dikenal."
    fi
    
    # Operator perbandingan
    if [ $ANGKA -gt 10 ]; then        # Greater than
        echo "Angka lebih besar dari 10"
    elif [ $ANGKA -eq 10 ]; then      # Equal
        echo "Angka sama dengan 10"
    else
        echo "Angka kurang dari 10"
    fi
    
    # Memeriksa file
    if [ -f "/etc/passwd" ]; then     # File exists
        echo "File passwd ditemukan"
    fi
    
    if [ -d "/home" ]; then           # Directory exists
        echo "Direktori /home ada"
    fi
    ```
    
- **Loop (for, while):**
    
    ```bash
    # For loop dengan list
    for i in 1 2 3 4 5; do
        echo "Angka: $i"
    done
    
    # For loop dengan range
    for i in {1..10}; do
        echo "Angka: $i"
    done
    
    # For loop dengan file
    for file in *.txt; do
        echo "Processing: $file"
    done
    
    # While loop
    COUNT=0
    while [ $COUNT -lt 5 ]; do
        echo "Hitungan: $COUNT"
        COUNT=$((COUNT + 1))
    done
    
    # Infinite loop dengan break
    while true; do
        read -p "Masukkan 'quit' untuk keluar: " input
        if [ "$input" == "quit" ]; then
            break
        fi
        echo "Anda mengetik: $input"
    done
    ```
    
- **Case statement:**
    
    ```bash
    echo "Pilih opsi (1-3):"
    read choice
    
    case $choice in
        1)
            echo "Anda memilih opsi 1"
            ;;
        2)
            echo "Anda memilih opsi 2"
            ;;
        3)
            echo "Anda memilih opsi 3"
            ;;
        *)
            echo "Opsi tidak valid"
            ;;
    esac
    ```
    

### Fungsi

- **Mendefinisikan dan menggunakan fungsi:**
    
    ```bash
    # Definisi fungsigreeting() {    echo "Halo dari fungsi!"}# Fungsi dengan parametersay_hello() {    local name=$1  # Parameter pertama    local age=$2   # Parameter kedua    echo "Halo $name, umur $age tahun"}# Fungsi dengan return valueadd_numbers() {    local num1=$1    local num2=$2    local result=$((num1 + num2))    echo $result  # Return via echo}# Memanggil fungsigreetingsay_hello "Budi" 25result=$(add_numbers 5 3)echo "Hasil: $result"
    ```
    

### Array

- **Array sederhana:**
    
    ```bash
    # Membuat arrayfruits=("apple" "banana" "orange")# Mengakses elemenecho ${fruits[0]}      # appleecho ${fruits[1]}      # banana# Semua elemenecho ${fruits[@]}      # Semua elemenecho ${#fruits[@]}     # Jumlah elemen# Loop melalui arrayfor fruit in "${fruits[@]}"; do    echo "Buah: $fruit"done
    ```
    

### Error Handling

- **Exit codes dan error handling:**
    
    ```bash
    # Memeriksa exit codecommand_that_might_failif [ $? -eq 0 ]; then    echo "Perintah berhasil"else    echo "Perintah gagal"fi# Menggunakan && dan ||mkdir /tmp/mydir && echo "Direktori dibuat" || echo "Gagal membuat direktori"# Set script untuk berhenti jika ada errorset -e  # Exit on errorset -u  # Exit on undefined variable# Trap untuk cleanupcleanup() {    echo "Membersihkan file temporary..."    rm -f /tmp/script_temp_*}trap cleanup EXIT
    ```
    

### Contoh Script Lanjutan

#### 1. Script Monitoring Sistem

```bash
#!/bin/bash

# Script monitoring sistem sederhana

LOG_FILE="/var/log/system_monitor.log"
THRESHOLD_CPU=80
THRESHOLD_MEM=80
THRESHOLD_DISK=90

log_message() {
    echo "$(date '+%Y-%m-%d %H:%M:%S') - $1" >> $LOG_FILE
}

check_cpu() {
    cpu_usage=$(top -bn1 | grep "Cpu(s)" | awk '{print $2}' | awk -F'%' '{print $1}')
    cpu_usage=${cpu_usage%.*}  # Remove decimal part
    
    if [ $cpu_usage -gt $THRESHOLD_CPU ]; then
        log_message "WARNING: CPU usage is ${cpu_usage}%"
        echo "CPU usage tinggi: ${cpu_usage}%"
    fi
}

check_memory() {
    mem_usage=$(free | grep Mem | awk '{printf "%.0f", $3/$2 * 100.0}')
    
    if [ $mem_usage -gt $THRESHOLD_MEM ]; then
        log_message "WARNING: Memory usage is ${mem_usage}%"
        echo "Memory usage tinggi: ${mem_usage}%"
    fi
}

check_disk() {
    while read line; do
        usage=$(echo $line | awk '{print $5}' | sed 's/%//')
        partition=$(echo $line | awk '{print $6}')
        
        if [ $usage -gt $THRESHOLD_DISK ]; then
            log_message "WARNING: Disk usage on $partition is ${usage}%"
            echo "Disk usage tinggi pada $partition: ${usage}%"
        fi
    done < <(df -h | grep -vE '^Filesystem|tmpfs|cdrom')
}

main() {
    echo "=== System Monitoring Report ==="
    echo "Waktu: $(date)"
    echo
    
    check_cpu
    check_memory
    check_disk
    
    echo "Monitoring selesai. Log tersimpan di $LOG_FILE"
}

# Jalankan fungsi main
main
```

#### 2. Script Backup Otomatis

```bash
#!/bin/bash

# Script backup otomatis dengan rotasi file

# Konfigurasi
SOURCE_DIRS=("/home/user/documents" "/home/user/projects" "/etc")
BACKUP_BASE_DIR="/var/backups"
RETENTION_DAYS=7
DATE=$(date +%Y%m%d_%H%M%S)
LOG_FILE="/var/log/backup.log"

# Fungsi logging
log() {
    echo "$(date '+%Y-%m-%d %H:%M:%S') - $1" | tee -a $LOG_FILE
}

# Fungsi untuk membuat backup
create_backup() {
    local source_dir=$1
    local dir_name=$(basename $source_dir)
    local backup_dir="$BACKUP_BASE_DIR/$dir_name"
    local backup_file="$backup_dir/backup_${dir_name}_${DATE}.tar.gz"
    
    # Buat direktori backup jika belum ada
    if [ ! -d "$backup_dir" ]; then
        mkdir -p "$backup_dir"
        log "Created backup directory: $backup_dir"
    fi
    
    # Buat backup
    log "Starting backup of $source_dir"
    if tar -czf "$backup_file" -C "$(dirname $source_dir)" "$(basename $source_dir)" 2>/dev/null; then
        log "Backup successful: $backup_file"
        
        # Hitung ukuran backup
        size=$(du -h "$backup_file" | cut -f1)
        log "Backup size: $size"
        
        return 0
    else
        log "ERROR: Backup failed for $source_dir"
        return 1
    fi
}

# Fungsi untuk menghapus backup lama
cleanup_old_backups() {
    local backup_dir=$1
    
    log "Cleaning up backups older than $RETENTION_DAYS days in $backup_dir"
    
    find "$backup_dir" -name "backup_*.tar.gz" -type f -mtime +$RETENTION_DAYS -delete
    
    local deleted_count=$(find "$backup_dir" -name "backup_*.tar.gz" -type f -mtime +$RETENTION_DAYS | wc -l)
    if [ $deleted_count -gt 0 ]; then
        log "Deleted $deleted_count old backup files"
    fi
}

# Fungsi untuk mengirim notifikasi
send_notification() {
    local message=$1
    local status=$2
    
    # Kirim ke syslog
    logger -t "backup_script" "$message"
    
    # Atau kirim email jika dikonfigurasi
    # echo "$message" | mail -s "Backup Report - $status" admin@example.com
}

# Fungsi utama
main() {
    log "=== Starting backup process ==="
    
    local success_count=0
    local fail_count=0
    
    # Pastikan direktori backup utama ada
    if [ ! -d "$BACKUP_BASE_DIR" ]; then
        mkdir -p "$BACKUP_BASE_DIR"
        log "Created main backup directory: $BACKUP_BASE_DIR"
    fi
    
    # Backup setiap direktori
    for source_dir in "${SOURCE_DIRS[@]}"; do
        if [ -d "$source_dir" ]; then
            if create_backup "$source_dir"; then
                ((success_count++))
                
                # Cleanup backup lama
                local dir_name=$(basename $source_dir)
                cleanup_old_backups "$BACKUP_BASE_DIR/$dir_name"
            else
                ((fail_count++))
            fi
        else
            log "WARNING: Source directory not found: $source_dir"
            ((fail_count++))
        fi
    done
    
    # Summary
    log "=== Backup process completed ==="
    log "Successful backups: $success_count"
    log "Failed backups: $fail_count"
    
    # Kirim notifikasi
    if [ $fail_count -eq 0 ]; then
        send_notification "All backups completed successfully" "SUCCESS"
    else
        send_notification "Backup completed with $fail_count failures" "WARNING"
    fi
}

# Jalankan script
main "$@"
```

#### 3. Script Setup Server Web

```bash
#!/bin/bash

# Script untuk setup server web LAMP stack

# Warna untuk output
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
NC='\033[0m' # No Color

# Fungsi untuk print dengan warna
print_status() {
    echo -e "${GREEN}[INFO]${NC} $1"
}

print_warning() {
    echo -e "${YELLOW}[WARNING]${NC} $1"
}

print_error() {
    echo -e "${RED}[ERROR]${NC} $1"
}

# Fungsi untuk check apakah script dijalankan sebagai root
check_root() {
    if [ "$EUID" -ne 0 ]; then
        print_error "Script ini harus dijalankan sebagai root"
        exit 1
    fi
}

# Update sistem
update_system() {
    print_status "Updating system packages..."
    apt update && apt upgrade -y
    
    if [ $? -eq 0 ]; then
        print_status "System updated successfully"
    else
        print_error "Failed to update system"
        exit 1
    fi
}

# Install Apache
install_apache() {
    print_status "Installing Apache web server..."
    apt install apache2 -y
    
    # Enable dan start Apache
    systemctl enable apache2
    systemctl start apache2
    
    # Check status
    if systemctl is-active --quiet apache2; then
        print_status "Apache installed and running"
    else
        print_error "Failed to start Apache"
        exit 1
    fi
}

# Install MySQL
install_mysql() {
    print_status "Installing MySQL server..."
    apt install mysql-server -y
    
    # Enable dan start MySQL
    systemctl enable mysql
    systemctl start mysql
    
    if systemctl is-active --quiet mysql; then
        print_status "MySQL installed and running"
        print_warning "Don't forget to run 'mysql_secure_installation'"
    else
        print_error "Failed to start MySQL"
        exit 1
    fi
}

# Install PHP
install_php() {
    print_status "Installing PHP and common modules..."
    apt install php libapache2-mod-php php-mysql php-curl php-gd php-json php-zip php-mbstring -y
    
    # Restart Apache untuk load PHP module
    systemctl restart apache2
    
    # Test PHP installation
    echo "<?php phpinfo(); ?>" > /var/www/html/info.php
    
    print_status "PHP installed successfully"
    print_status "You can test PHP at http://your-server-ip/info.php"
}

# Configure firewall
configure_firewall() {
    print_status "Configuring firewall..."
    
    # Install UFW jika belum ada
    apt install ufw -y
    
    # Basic firewall rules
    ufw default deny incoming
    ufw default allow outgoing
    ufw allow ssh
    ufw allow 'Apache Full'
    
    # Enable firewall
    ufw --force enable
    
    print_status "Firewall configured"
}

# Create virtual host
create_vhost() {
    local domain=$1
    local doc_root="/var/www/$domain"
    
    print_status "Creating virtual host for $domain..."
    
    # Buat direktori document root
    mkdir -p $doc_root
    
    # Buat file index sederhana
    cat > $doc_root/index.html << EOF
<!DOCTYPE html>
<html>
<head>
    <title>Welcome to $domain</title>
</head>
<body>
    <h1>Welcome to $domain</h1>
    <p>This is a default page for $domain</p>
    <p>Server is running PHP $(php -v | head -n1 | cut -d" " -f2)</p>
</body>
</html>
EOF

    # Buat konfigurasi virtual host
    cat > /etc/apache2/sites-available/$domain.conf << EOF
<VirtualHost *:80>
    ServerName $domain
    ServerAlias www.$domain
    DocumentRoot $doc_root
    
    <Directory $doc_root>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    
    ErrorLog \${APACHE_LOG_DIR}/${domain}_error.log
    CustomLog \${APACHE_LOG_DIR}/${domain}_access.log combined
</VirtualHost>
EOF

    # Enable site
    a2ensite $domain.conf
    
    # Set permissions
    chown -R www-data:www-data $doc_root
    chmod -R 755 $doc_root
    
    # Restart Apache
    systemctl restart apache2
    
    print_status "Virtual host created for $domain"
}

# Fungsi untuk menampilkan summary
show_summary() {
    print_status "=== LAMP Stack Installation Complete ==="
    echo
    print_status "Services Status:"
    systemctl is-active apache2 && echo "  Apache: Running" || echo "  Apache: Not Running"
    systemctl is-active mysql && echo "  MySQL: Running" || echo "  MySQL: Not Running"
    echo
    print_status "Important Files:"
    echo "  Apache config: /etc/apache2/"
    echo "  Web root: /var/www/html/"
    echo "  PHP info: http://your-server-ip/info.php"
    echo
    print_status "Next Steps:"
    echo "  1. Run 'mysql_secure_installation' to secure MySQL"
    echo "  2. Remove /var/www/html/info.php when done testing"
    echo "  3. Configure your domain/DNS settings"
}

# Menu utama
show_menu() {
    echo "=== LAMP Stack Setup Script ==="
    echo "1. Install Full LAMP Stack"
    echo "2. Install Apache only"
    echo "3. Install MySQL only"
    echo "4. Install PHP only"
    echo "5. Create Virtual Host"
    echo "6. Exit"
    echo
    read -p "Choose an option [1-6]: " choice
    
    case $choice in
        1)
            update_system
            install_apache
            install_mysql
            install_php
            configure_firewall
            show_summary
            ;;
        2)
            install_apache
            ;;
        3)
            install_mysql
            ;;
        4)
            install_php
            ;;
        5)
            read -p "Enter domain name: " domain
            create_vhost $domain
            ;;
        6)
            print_status "Exiting..."
            exit 0
            ;;
        *)
            print_error "Invalid option"
            show_menu
            ;;
    esac
}

# Main function
main() {
    check_root
    show_menu
}

# Jalankan script
main "$@"
```

### Tips Shell Scripting

1. **Debugging:**
    
    ```bash
    bash -x script.sh     # Debug mode
    set -x               # Enable debug dalam script
    set +x               # Disable debug
    ```
    
2. **Best Practices:**
    
    - Selalu gunakan quotes untuk variabel: `"$variable"`
    - Gunakan `set -e` untuk exit on error
    - Gunakan `set -u` untuk exit on undefined variable
    - Beri nama variable yang deskriptif
    - Gunakan fungsi untuk kode yang berulang
    - Tambahkan help/usage function
    - Validasi input pengguna
3. **Testing Script:**
    
    ```bash
    # Test dengan dry run
    if [ "$1" == "--dry-run" ]; then
        echo "This would run: $command"
    else
        $command
    fi
    ```
    

## Pipes dan Redirection

Pipes dan redirection adalah fitur powerful Linux untuk menggabungkan perintah dan mengarahkan input/output.

### Redirection

- **Output Redirection:**
    
    ```bash
    echo "Hello" > file.txt          # Tulis ke file (overwrite)
    echo "World" >> file.txt         # Tambah ke file (append)
    ls /nonexistent 2> error.txt     # Redirect error ke file
    ls /home > output.txt 2>&1       # Redirect output dan error ke file
    ls /home &> all_output.txt       # Shorthand untuk redirect semua
    ```
    
- **Input Redirection:**
    
    ```bash
    wc -l < file.txt                 # Input dari file
    mysql -u root -p < backup.sql    # Input SQL dari file
    ```
    
- **Here Documents:**
    
    ```bash
    cat << EOF > config.txt
    server_name = localhost
    port = 8080
    debug = true
    EOF
    ```
    

### Pipes

- **Basic Pipes:**
    
    ```bash
    ls -la | grep "txt"              # Filter output ls
    ps aux | grep apache             # Cari proses apache
    cat logfile.txt | tail -n 20     # 20 baris terakhir
    ```
    
- **Complex Pipe Chains:**
    
    ```bash
    # Cari file terbesar
    du -ah /home | sort -rh | head -10
    
    # Analisis log Apache
    cat /var/log/apache2/access.log | awk '{print $1}' | sort | uniq -c | sort -rn | head -10
    
    # Monitor proses real-time
    ps aux | sort -rk 3,3 | head -10
    ```
    
- **Tee Command:** Menulis ke file dan stdout bersamaan.
    
    ```bash
    ls -la | tee output.txt          # Tampilkan di layar dan simpan ke file
    echo "log entry" | tee -a log.txt # Append ke file dan tampilkan
    ```
    

## Text Processing

Linux menyediakan banyak tools untuk memproses text yang sangat berguna untuk analisis log dan data.

### AWK

AWK adalah bahasa pemrograman untuk pemrosesan pola dan data.

- **Basic AWK:**
    
    ```bash
    awk '{print $1}' file.txt        # Print kolom pertama
    awk '{print $1, $3}' file.txt    # Print kolom 1 dan 3
    awk '{print NF}' file.txt        # Print jumlah field per baris
    awk '{print NR, $0}' file.txt    # Print nomor baris dan isi baris
    ```
    
- **AWK dengan kondisi:**
    
    ```bash
    awk '$3 > 100 {print $1, $3}' file.txt    # Print jika kolom 3 > 100
    awk '/error/ {print $0}' logfile.txt      # Print baris yang mengandung "error"
    awk 'length($0) > 80' file.txt            # Print baris lebih dari 80 karakter
    ```
    
- **AWK untuk analisis log:**
    
    ```bash
    # Hitung request per IP dari log Apache
    awk '{print $1}' /var/log/apache2/access.log | sort | uniq -c | sort -rn
    
    # Status code dari log Apache
    awk '{print $9}' /var/log/apache2/access.log | sort | uniq -c
    
    # Bandwidth usage
    awk '{sum += $10} END {print "Total bytes:", sum}' /var/log/apache2/access.log
    ```
    

### SED

SED (Stream Editor) untuk editing text secara batch.

- **Basic SED:**
    
    ```bash
    sed 's/old/new/' file.txt           # Replace pertama kali per baris
    sed 's/old/new/g' file.txt          # Replace semua occurrence
    sed 's/old/new/gi' file.txt         # Replace case-insensitive
    sed -i 's/old/new/g' file.txt       # Edit file in-place
    ```
    
- **SED advanced:**
    
    ```bash
    sed '2d' file.txt                    # Hapus baris ke-2
    sed '2,5d' file.txt                  # Hapus baris 2-5
    sed '/pattern/d' file.txt            # Hapus baris yang match pattern
    sed -n '2,5p' file.txt               # Print hanya baris 2-5
    sed 'G' file.txt                     # Tambah baris kosong setelah setiap baris
    ```
    
- **SED untuk konfigurasi:**
    
    ```bash
    # Uncomment line in config
    sed -i 's/^#\(.*option.*\)/\1/' config.file
    
    # Change configuration value
    sed -i 's/^port=.*/port=8080/' config.file
    ```
    

### CUT

Mengekstrak kolom atau karakter dari text.

- **Basic CUT:**
    
    ```bash
    cut -d: -f1 /etc/passwd             # Field 1 dengan delimiter :cut -d: -f1,3 /etc/passwd           # Field 1 dan 3cut -c1-10 file.txt                 # Karakter 1-10cut -d' ' -f2- file.txt             # Field 2 sampai akhir
    ```
    

### TR

Translate atau delete karakter.

- **Basic TR:**
    
    ```bash
    tr 'a-z' 'A-Z' < file.txt          # Convert ke uppercasetr -d '0-9' < file.txt              # Hapus semua angkatr -s ' ' < file.txt                # Squeeze multiple spaces menjadi satutr ' ' '\n' < file.txt              # Replace space dengan newline
    ```
    

## Cron Jobs dan Task Scheduling

Cron adalah service untuk menjalankan perintah secara otomatis pada waktu tertentu.

### Crontab Format

Format crontab: `minute hour day month day_of_week command`

```
* * * * * command
│ │ │ │ │
│ │ │ │ └─── Day of week (0-7, Sunday = 0 or 7)
│ │ │ └───── Month (1-12)
│ │ └─────── Day of month (1-31)
│ └───────── Hour (0-23)
└─────────── Minute (0-59)
```

### Mengelola Crontab

- **Melihat dan mengedit crontab:**
    
    ```bash
    crontab -l                          # List crontab user saat ini
    crontab -e                          # Edit crontab
    crontab -r                          # Remove semua crontab
    sudo crontab -l -u username         # List crontab user lain
    ```
    
- **Contoh crontab entries:**
    
    ```bash
    # Backup setiap hari jam 2 pagi
    0 2 * * * /home/user/backup.sh
    
    # Update sistem setiap Minggu jam 1 pagi
    0 1 * * 0 apt update && apt upgrade -y
    
    # Restart web server setiap 6 jam
    0 */6 * * * systemctl restart apache2
    
    # Cleanup log files setiap bulan
    0 0 1 * * find /var/log -name "*.log" -mtime +30 -delete
    
    # Monitor disk space setiap 15 menit
    */15 * * * * df -h | mail -s "Disk Usage Report" admin@example.com
    ```
    
- **Special time specifications:**
    
    ```bash
    @reboot /path/to/startup-script.sh    # Saat boot
    @daily /path/to/daily-task.sh         # Setiap hari
    @weekly /path/to/weekly-task.sh       # Setiap minggu
    @monthly /path/to/monthly-task.sh     # Setiap bulan
    @hourly /path/to/hourly-task.sh       # Setiap jam
    ```
    

### System-wide Cron

- **Cron directories:**
    
    ```bash
    /etc/cron.d/        # Additional cron files
    /etc/cron.daily/    # Daily scripts
    /etc/cron.weekly/   # Weekly scripts
    /etc/cron.monthly/  # Monthly scripts
    /etc/cron.hourly/   # Hourly scripts
    ```
    
- **Membuat script untuk cron.daily:**
    
    ```bash
    sudo nano /etc/cron.daily/system-maintenance
    ```
    
    ```bash
    #!/bin/bash
    
    # Clean package cache
    apt autoremove -y
    apt autoclean
    
    # Update locate database
    updatedb
    
    # Clean temporary files
    find /tmp -type f -mtime +7 -delete
    
    # Log the maintenance
    echo "$(date): System maintenance completed" >> /var/log/maintenance.log
    ```
    
    ```bash
    sudo chmod +x /etc/cron.daily/system-maintenance
    ```
    

## Kompresi dan Arsip

### TAR (Tape Archive)

- **Membuat arsip:**
    
    ```bash
    tar -cf archive.tar files/          # Buat tar archive
    tar -czf archive.tar.gz files/      # Buat tar.gz (compressed)
    tar -cjf archive.tar.bz2 files/     # Buat tar.bz2 (better compression)
    tar -caf archive.tar.xz files/      # Auto-detect compression
    ```
    
- **Ekstrak arsip:**
    
    ```bash
    tar -xf archive.tar                 # Ekstrak tar
    tar -xzf archive.tar.gz             # Ekstrak tar.gz
    tar -xjf archive.tar.bz2            # Ekstrak tar.bz2
    tar -xf archive.tar.xz              # Ekstrak tar.xz
    ```
    
- **Melihat isi arsip:**
    
    ```bash
    tar -tf archive.tar                 # List contents
    tar -tzf archive.tar.gz             # List contents of compressed
    ```
    
- **Ekstrak file tertentu:**
    
    ```bash
    tar -xzf archive.tar.gz specific-file.txt
    tar -xzf archive.tar.gz --wildcards "*.conf"
    ```
    

### ZIP/UNZIP

- **Membuat ZIP:**
    
    ```bash
    zip -r archive.zip folder/          # Recursive zip
    zip archive.zip file1.txt file2.txt # Zip specific files
    zip -e secure.zip sensitive-data/   # Password protected
    ```
    
- **Ekstrak ZIP:**
    
    ```bash
    unzip archive.zip                   # Ekstrak semua
    unzip archive.zip -d /target/dir/   # Ekstrak ke direktori tertentu
    unzip -l archive.zip                # List contents
    unzip archive.zip "*.txt"           # Ekstrak hanya file txt
    ```
    

### Kompresi Individual Files

- **GZIP:**
    
    ```bash
    gzip file.txt                       # Compress file.txt -> file.txt.gz
    gzip -d file.txt.gz                 # Decompress
    gunzip file.txt.gz                  # Alternative decompress
    gzip -c file.txt > compressed.gz    # Keep original file
    ```
    
- **BZIP2:**
    
    ```bash
    bzip2 file.txt                      # Compress
    bzip2 -d file.txt.bz2               # Decompress
    bunzip2 file.txt.bz2                # Alternative decompress
    ```
    

## Environment Variables dan PATH

### Mengelola Environment Variables

- **Melihat environment variables:**
    
    ```bash
    env                                 # Semua environment variables
    printenv                            # Alternative
    echo $HOME                          # Variable tertentu
    echo $PATH                          # PATH variable
    ```
    
- **Set temporary variables:**
    
    ```bash
    export MYVAR="Hello World"          # Set untuk session saat ini
    echo $MYVAR                         # Display value
    ```
    
- **Set permanent variables:**
    
    ```bash
    # Untuk user tertentu - edit ~/.bashrc atau ~/.profile
    echo 'export MYVAR="Hello World"' >> ~/.bashrc
    source ~/.bashrc                    # Reload
    
    # Untuk semua user - edit /etc/environment
    echo 'MYVAR="Hello World"' | sudo tee -a /etc/environment
    ```
    
- **Menambah ke PATH:**
    
    ```bash
    # Temporary
    export PATH=$PATH:/new/path
    
    # Permanent - tambah ke ~/.bashrc
    echo 'export PATH=$PATH:/new/path' >> ~/.bashrc
    ```
    

### Konfigurasi Shell

- **File konfigurasi penting:**
    
    ```bash
    ~/.bashrc           # Bash configuration for interactive non-login shells
    ~/.bash_profile     # Bash configuration for login shells
    ~/.profile          # Shell-agnostic configuration
    /etc/bash.bashrc    # System-wide bash configuration
    /etc/profile        # System-wide shell configuration
    ```
    
- **Alias:**
    
    ```bash
    # Temporary alias
    alias ll='ls -la'
    alias la='ls -A'
    alias grep='grep --color=auto'
    
    # Permanent alias - tambah ke ~/.bashrc
    echo "alias ll='ls -la'" >> ~/.bashrc
    ```
    
- **Custom functions dalam .bashrc:**
    
    ```bash
    # Tambahkan ke ~/.bashrc
    function mkcd() {
        mkdir -p "$1" && cd "$1"
    }
    
    function extract() {
        if [ -f "$1" ]; then
            case "$1" in
                *.tar.bz2)   tar xjf "$1";;
                *.tar.gz)    tar xzf "$1";;
                *.bz2)       bunzip2 "$1";;
                *.rar)       unrar x "$1";;
                *.gz)        gunzip "$1";;
                *.tar)       tar xf "$1";;
                *.tbz2)      tar xjf "$1";;
                *.tgz)       tar xzf "$1";;
                *.zip)       unzip "$1";;
                *.Z)         uncompress "$1";;
                *.7z)        7z x "$1";;
                *)           echo "Don't know how to extract '$1'";;
            esac
        else
            echo "'$1' is not a valid file!"
        fi
    }
    ```
    

## Tips Productivity dan Best Practices

### Keyboard Shortcuts Penting

- **Terminal shortcuts:**
    
    ```bash
    Ctrl + C            # Interrupt/kill process
    Ctrl + Z            # Suspend process
    Ctrl + D            # EOF/logout
    Ctrl + L            # Clear screen
    Ctrl + A            # Beginning of line
    Ctrl + E            # End of line
    Ctrl + U            # Clear line before cursor
    Ctrl + K            # Clear line after cursor
    Ctrl + W            # Delete word before cursor
    Ctrl + R            # Reverse search history
    Ctrl + G            # Exit search
    ```
    
- **History shortcuts:**
    
    ```bash
    !!                  # Last command
    !n                  # Command number n from history
    !string             # Last command starting with string
    ^old^new            # Replace old with new in last command
    ```
    

### Command History

- **Mengelola history:**
    
    ```bash
    history                             # Show command history
    history | grep ssh                  # Search history
    !1234                              # Execute command number 1234
    ```
    
- **Konfigurasi history:**
    
    ```bash
    # Tambah ke ~/.bashrc
    HISTSIZE=10000                     # Lines in memory
    HISTFILESIZE=20000                 # Lines in history file
    HISTCONTROL=ignoredups:ignorespace # Ignore duplicates and commands starting with space
    ```
    

### File Operations Tips

- **Bulk operations:**
    
    ```bash
    # Rename multiple files
    for file in *.txt; do mv "$file" "${file%.txt}.bak"; done
    
    # Change extension
    rename 's/\.txt$/.bak/' *.txt
    
    # Create multiple directories
    mkdir -p project/{src,tests,docs,config}
    
    # Copy with progress
    rsync -av --progress source/ destination/
    ```
    
- **Find and execute:**
    
    ```bash
    # Find and delete
    find /path -name "*.tmp" -delete
    
    # Find and execute command
    find /path -name "*.log" -exec gzip {} \;
    
    # Find with multiple conditions
    find /var/log -name "*.log" -size +100M -mtime +30
    ```
    

## Troubleshooting dan Debugging

### System Information

- **Hardware information:**
    
    ```bash
    lscpu                              # CPU info
    lsmem                              # Memory info
    lsblk                              # Block devices
    lspci                              # PCI devices
    lsusb                              # USB devices
    dmidecode                          # Hardware details
    ```
    
- **System information:**
    
    ```bash
    uname -a                           # Kernel info
    cat /etc/os-release                # OS info
    uptime                             # System uptime
    who                                # Logged in users
    last                               # Login history
    ```
    

### Performance Monitoring

- **Real-time monitoring:**
    
    ```bash
    top                                # Process monitor
    htop                               # Better process monitor
    iotop                              # I/O monitor
    nethogs                            # Network usage by process
    ```
    
- **System statistics:**
    
    ```bash
    vmstat 1                           # Virtual memory stats
    iostat 1                           # I/O stats
    sar 1 10                           # System activity reporter
    ```
    

### Log Analysis

- **Important log files:**
    
    ```bash
    /var/log/syslog                    # System messages
    /var/log/auth.log                  # Authentication logs
    /var/log/kern.log                  # Kernel messages
    /var/log/apache2/error.log         # Apache errors
    /var/log/mysql/error.log           # MySQL errors
    ```
    
- **Log analysis commands:**
    
    ```bash
    # Real-time log monitoring
    tail -f /var/log/syslog
    
    # Search for errors
    grep -i error /var/log/syslog
    
    # Count error occurrences
    grep -c "error" /var/log/apache2/error.log
    
    # Show logs from specific time
    journalctl --since "2023-07-27 10:00:00"
    ```
    

## Keterkaitan dengan Networking dan Cloud Computing

Pemahaman Linux yang mendalam sangat penting untuk:

### Network Administration

1. **Server Management:** Sebagian besar server web, DNS, dan aplikasi jaringan berjalan di Linux
2. **Router dan Firewall:** Banyak perangkat jaringan berbasis Linux
3. **Monitoring Tools:** Wireshark, tcpdump, dan tools monitoring lainnya optimal di Linux
4. **Automation:** Script automation untuk konfigurasi jaringan dan maintenance

### Cloud Computing

1. **Virtual Machines:** Mayoritas VM di cloud provider (AWS, Google Cloud, Azure) menggunakan Linux
2. **Containers:** Docker dan Kubernetes berjalan optimal di Linux
3. **DevOps:** CI/CD pipelines menggunakan Linux untuk automation
4. **Microservices:** Arsitektur microservices biasanya di-deploy di Linux containers

### Cybersecurity

1. **Penetration Testing:** Tools seperti Kali Linux untuk security testing
2. **Log Analysis:** Analisis keamanan melalui system logs
3. **Incident Response:** Forensik dan response menggunakan Linux tools
4. **Hardening:** Mengamankan sistem Linux untuk production

### Praktikum dan Latihan

#### Latihan 1: Administrasi Dasar

1. Buat struktur direktori project dengan berbagai file
2. Set permissions yang appropriate
3. Buat users dan groups
4. Konfigurasi sudo access

#### Latihan 2: Monitoring dan Logging

1. Setup log rotation
2. Buat script monitoring system resources
3. Konfigurasi alerting sederhana
4. Analisis log files

#### Latihan 3: Automation

1. Buat script backup otomatis
2. Setup cron jobs
3. Buat script deployment sederhana
4. Implement error handling dan logging

#### Latihan 4: Network Services

1. Install dan konfigurasi web server
2. Setup virtual hosts
3. Konfigurasi firewall
4. Monitor network connections

### Sertifikasi dan Pembelajaran Lanjutan

1. **CompTIA Linux+:** Sertifikasi dasar untuk Linux administration
2. **RHCSA/RHCE:** Red Hat certification untuk enterprise Linux
3. **LPIC:** Linux Professional Institute certification
4. **Cloud certifications:** AWS/GCP/Azure yang memerlukan Linux knowledge

### Resources Tambahan

1. **Dokumentasi:**
    
    - Man pages: `man command`
    - Info pages: `info command`
    - `/usr/share/doc/` directory
2. **Online Resources:**
    
    - Linux Documentation Project
    - ArchWiki (sangat comprehensive)
    - Ubuntu Documentation
    - Red Hat documentation
3. **Books:**
    
    - "The Linux Command Line" by William Shotts
    - "UNIX and Linux System Administration Handbook"
    - "Linux Bible" by Christopher Negus

Dengan menguasai dasar-dasar Linux ini, siswa SMK akan memiliki foundation yang kuat untuk berkarir di bidang IT, khususnya networking, cloud computing, dan cybersecurity. Linux bukan hanya sistem operasi, tetapi ekosistem yang mendukung infrastruktur teknologi modern.