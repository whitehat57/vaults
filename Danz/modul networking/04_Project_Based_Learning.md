# Modul 4: Proyek Berbasis Pembelajaran - Server Web Pribadi di Cloud

## Pengantar Proyek

Proyek ini akan memandu Siswa membangun dan mengkonfigurasi server web pribadi menggunakan teknologi *open-source* di lingkungan *cloud*. Ini adalah aplikasi praktis dari konsep-konsep yang telah Siswa pelajari di modul Linux, Networking, dan Cloud Computing. Dengan menyelesaikan proyek ini, Siswa akan memiliki server web yang dapat diakses dari mana saja di internet, menunjukkan pemahaman Siswa tentang infrastruktur modern.

**Tujuan Pembelajaran Proyek:**
Setelah menyelesaikan proyek ini, siswa akan dapat:
*   Memilih dan menyediakan *Virtual Machine* (VM) Linux di platform cloud.
*   Mengakses dan mengkonfigurasi sistem operasi Linux dasar pada VM.
*   Menginstal dan mengkonfigurasi server web *open-source* (Nginx atau Apache) di Linux.
*   Memahami dan menerapkan konsep jaringan seperti alamat IP, port, dan DNS dalam konteks cloud.
*   Mengkonfigurasi aturan *firewall* (Security Group/NACL) di lingkungan cloud untuk mengamankan server web.
*   Mengakses server web dari internet menggunakan alamat IP publik atau nama domain.

**Alat dan Teknologi yang Digunakan :**
*   **Sistem Operasi:** Ubuntu Server (distribusi Linux *open-source*).
*   **Penyedia Cloud:** Siswa dapat menggunakan *free tier* dari penyedia cloud seperti AWS, Google Cloud Platform, atau Microsoft Azure. Modul ini akan memberikan panduan umum yang dapat diadaptasi.
*   **Akses Jarak Jauh:** SSH (Secure Shell) client (tersedia di Linux/macOS secara *default*, atau PuTTY/WSL di Windows).
*   **Server Web:** Nginx atau Apache HTTP Server (keduanya *open-source*). Kami akan fokus pada Nginx dalam panduan ini.
*   **Alat Jaringan Linux:** `ping`, `curl`, `netstat`, `ip a`, `dig`.
*   **Editor Teks:** Nano atau Vim (di Linux VM).

## Langkah 1: Perencanaan Infrastruktur Cloud

Sebelum memulai, mari rencanakan infrastruktur dasar yang akan kita gunakan.

### Memilih Penyedia Cloud dan Jenis VM

Pilih salah satu penyedia cloud yang menawarkan *free tier* untuk VM:
*   **Amazon Web Services (AWS):** Layanan EC2 (Elastic Compute Cloud) dengan *instance* t2.micro atau t3.micro (termasuk dalam *free tier*).
*   **Google Cloud Platform (GCP):** Layanan Compute Engine dengan *instance* f1-micro (termasuk dalam *free tier*).
*   **Microsoft Azure:** Layanan Azure Virtual Machines dengan *instance* B1s (termasuk dalam *free tier*).

Untuk proyek ini, spesifikasi VM yang direkomendasikan adalah:
*   **CPU:** 1 vCPU
*   **RAM:** 1 GB
*   **Sistem Operasi:** Ubuntu Server (versi LTS terbaru, misalnya Ubuntu 22.04 LTS).
*   **Penyimpanan:** Minimal 8-10 GB SSD.

### Merencanakan Konfigurasi Jaringan Virtual

Setiap penyedia cloud memiliki konsep jaringan virtualnya sendiri (VPC di AWS, Virtual Network di Azure, VPC Network di GCP). Secara *default*, akun Siswa akan memiliki jaringan virtual yang sudah dikonfigurasi. Yang perlu Siswa perhatikan adalah:

*   **Subnet:** VM Siswa akan ditempatkan di sebuah subnet dalam jaringan virtual.
*   **IP Publik:** VM Siswa akan membutuhkan alamat IP publik agar dapat diakses dari internet.
*   **Security Group / Firewall Rules:** Ini adalah *firewall* tingkat jaringan yang akan mengontrol lalu lintas masuk dan keluar dari VM Siswa. Kita akan mengkonfigurasinya untuk mengizinkan SSH, HTTP, dan HTTPS.

### Memahami Model Biaya Dasar

Penting untuk memahami bahwa meskipun ada *free tier*, penggunaan di luar batas *free tier* akan dikenakan biaya. Selalu pantau penggunaan Siswa melalui konsol penyedia cloud. Untuk proyek ini, pastikan Siswa memilih *instance* yang termasuk dalam *free tier* dan matikan VM Siswa setelah selesai menggunakan untuk menghindari biaya tak terduga.

## Langkah 2: Penyediaan Mesin Virtual (VM) Linux

Langkah-langkah ini akan bervariasi sedikit tergantung penyedia cloud yang Siswa pilih, tetapi konsepnya sama.

1.  **Login ke Konsol Cloud:** Akses konsol manajemen penyedia cloud pilihan Siswa (AWS Management Console, Google Cloud Console, Azure Portal).
2.  **Buat VM Baru:**
    *   Cari layanan untuk membuat *Virtual Machine* (misalnya, "EC2" di AWS, "Compute Engine" di GCP, "Virtual Machines" di Azure).
    *   Pilih opsi untuk membuat *instance* atau VM baru.
3.  **Konfigurasi VM:**
    *   **Nama:** Berikan nama yang mudah diingat (misalnya, `my-web-server`).
    *   **Region/Zone:** Pilih lokasi geografis yang dekat dengan Siswa atau target audiens Siswa.
    *   **Image/OS:** Pilih **Ubuntu Server LTS** (misalnya, Ubuntu 22.04 LTS).
    *   **Instance Type/Machine Type:** Pilih tipe yang termasuk dalam *free tier* (misalnya, `t2.micro` di AWS, `f1-micro` di GCP, `B1s` di Azure).
    *   **Storage/Disk:** Biarkan *default* (biasanya 8-10 GB SSD sudah cukup).
    *   **Network Settings:**
        *   Pastikan VM mendapatkan **IP Publik**.
        *   **Security Group / Firewall Rules:** Ini adalah bagian krusial. Siswa perlu membuat atau mengkonfigurasi aturan *firewall* untuk mengizinkan:
            *   **SSH (Port 22 TCP):** Izinkan dari IP Siswa saja (lebih aman) atau dari `0.0.0.0/0` (semua IP, kurang aman tapi mudah untuk latihan).
            *   **HTTP (Port 80 TCP):** Izinkan dari `0.0.0.0/0`.
            *   **HTTPS (Port 443 TCP):** Izinkan dari `0.0.0.0/0`.
    *   **Key Pair (Kunci SSH):** Buat pasangan kunci SSH baru atau gunakan yang sudah ada. Ini sangat penting untuk mengakses VM Siswa dengan aman. Unduh file kunci privat (`.pem` atau `.ppk`) dan simpan di tempat yang aman.

4.  **Luncurkan/Buat VM:** Tinjau konfigurasi Siswa dan luncurkan VM. Tunggu beberapa menit hingga VM siap.

## Langkah 3: Konfigurasi Dasar Linux pada VM

Setelah VM berjalan, saatnya mengakses dan mengkonfigurasinya.

### Akses VM Menggunakan SSH

1.  **Buka Terminal Lokal:** Di Linux/macOS, buka aplikasi Terminal. Di Windows, gunakan WSL (Windows Subsystem for Linux) atau PuTTY.
2.  **Atur Izin Kunci SSH:** Pastikan file kunci privat Siswa memiliki izin yang benar (hanya dapat dibaca oleh pemilik).
    ```bash
    chmod 400 /path/to/your-key.pem
    ```
3.  **Akses VM via SSH:** Gunakan perintah `ssh`. Ganti `user` dengan nama pengguna *default* untuk Ubuntu (biasanya `ubuntu`), dan `your_vm_public_ip` dengan alamat IP publik VM Siswa.
    ```bash
    ssh -i /path/to/your-key.pem ubuntu@your_vm_public_ip
    ```
    Jika berhasil, Siswa akan masuk ke *command line* VM Linux Siswa.

### Pembaruan Sistem dan Instalasi Paket Dasar

Setelah masuk, langkah pertama adalah memperbarui daftar paket dan meng-upgrade sistem.

```bash
sudo apt update
sudo apt upgrade -y
```
Perintah `sudo` digunakan untuk menjalankan perintah dengan hak akses *root*. `apt` adalah manajer paket untuk Ubuntu.

### Manajemen Pengguna dan Izin File (Opsional, tapi Direkomendasikan)

Untuk keamanan dan praktik terbaik, Siswa bisa membuat pengguna baru dan mengatur izin.

1.  **Buat Pengguna Baru:**
    ```bash
    sudo useradd -m -s /bin/bash nama_pengguna_baru
    sudo passwd nama_pengguna_baru
    ```
    Ikuti petunjuk untuk mengatur kata sandi.
2.  **Tambahkan ke Grup `sudo`:** Agar pengguna baru dapat menjalankan perintah dengan `sudo`.
    ```bash
    sudo usermod -aG sudo nama_pengguna_baru
    ```
3.  **Keluar dan Login Kembali:** Keluar dari sesi SSH (`exit`) dan login kembali dengan pengguna baru Siswa.
    ```bash
    ssh -i /path/to/your-key.pem nama_pengguna_baru@your_vm_public_ip
    ```

## Langkah 4: Instalasi dan Konfigurasi Server Web (Nginx)

Pada langkah ini, kita akan menginstal dan mengkonfigurasi Nginx, sebuah server web *open-source* yang ringan dan efisien, di VM Linux Siswa. Nginx akan bertanggung jawab untuk menyajikan halaman web Siswa kepada pengunjung.

### 4.1. Instalasi Nginx

Sebelum menginstal Nginx, selalu disarankan untuk memperbarui daftar paket di sistem Siswa. Ini memastikan Siswa mendapatkan versi terbaru dari perangkat lunak dan dependensinya.

1.  **Perbarui Daftar Paket:**
    Perintah ini akan mengambil informasi terbaru tentang paket-paket yang tersedia dari repositori Ubuntu.
    ```bash
    sudo apt update
    ```
    *   **Penjelasan:**
        *   `sudo`: Digunakan untuk menjalankan perintah dengan hak akses *superuser* (administrator), karena instalasi paket memerlukan izin tinggi.
        *   `apt`: Adalah *Advanced Package Tool*, manajer paket *default* di Ubuntu.
        *   `update`: Memberi tahu `apt` untuk menyinkronkan indeks paket dari sumber yang telah ditentukan. Ini tidak menginstal atau memperbarui paket, hanya memperbarui daftar paket yang bisa diinstal.

2.  **Instal Nginx:**
    Setelah daftar paket diperbarui, Siswa bisa menginstal Nginx.
    ```bash
    sudo apt install nginx -y
    ```
    *   **Penjelasan:**
        *   `install nginx`: Memberi tahu `apt` untuk menginstal paket Nginx.
        *   `-y`: Opsi ini secara otomatis menjawab "ya" untuk setiap pertanyaan konfirmasi selama proses instalasi, sehingga proses berjalan tanpa interupsi.

    *   **Output yang Diharapkan:**
        Siswa akan melihat proses pengunduhan dan instalasi paket. Setelah selesai, Siswa akan kembali ke *prompt* terminal.

### 4.2. Verifikasi Status Nginx

Setelah instalasi, Nginx seharusnya sudah berjalan secara otomatis. Mari kita verifikasi statusnya.

1.  **Periksa Status Layanan Nginx:**
    ```bash
    sudo systemctl status nginx
    ```
    *   **Penjelasan:**
        *   `systemctl`: Adalah *utility* untuk mengontrol sistem dan manajer layanan `systemd` di Linux.
        *   `status nginx`: Meminta `systemctl` untuk menampilkan status layanan Nginx.

    *   **Output yang Diharapkan:**
        Siswa seharusnya melihat output yang mirip dengan ini, menunjukkan Nginx `active (running)`:
        ```
        ● nginx.service - A high performance web server and a reverse proxy server
             Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
             Active: active (running) since ...
               Docs: man:nginx(8)
            Process: ...
           Main PID: ...
              Tasks: ...
             Memory: ...
                CPU: ...
             CGroup: /system.slice/nginx.service
                     └─... nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
        ```
        Jika statusnya tidak `active (running)`, Siswa bisa mencoba memulai Nginx dengan perintah:
        ```bash
        sudo systemctl start nginx
        ```
        Dan untuk menghentikannya:
        ```bash
        sudo systemctl stop nginx
        ```

### 4.3. Konfigurasi Firewall Linux (UFW)

Meskipun Siswa sudah mengkonfigurasi *Security Group* di cloud, penting juga untuk mengkonfigurasi *firewall* lokal di VM Linux Siswa (UFW) sebagai lapisan keamanan tambahan. UFW (Uncomplicated Firewall) adalah antarmuka yang lebih mudah digunakan untuk `iptables`.

1.  **Izinkan Lalu Lintas HTTP dan HTTPS:**
    Nginx mendaftarkan profil aplikasi dengan UFW, yang memudahkan untuk mengizinkan lalu lintas ke server web.
    ```bash
    sudo ufw allow 'Nginx HTTP'
    sudo ufw allow 'Nginx HTTPS' # Ini untuk nanti jika Siswa mengimplementasikan HTTPS
    ```
    *   **Penjelasan:**
        *   `ufw allow 'Nginx HTTP'`: Mengizinkan lalu lintas masuk pada port 80 (HTTP) yang digunakan oleh Nginx.
        *   `ufw allow 'Nginx HTTPS'`: Mengizinkan lalu lintas masuk pada port 443 (HTTPS) yang digunakan oleh Nginx.

2.  **Izinkan Lalu Lintas SSH:**
    Pastikan Siswa masih bisa mengakses VM melalui SSH.
    ```bash
    sudo ufw allow 'OpenSSH'
    ```
    *   **Penjelasan:**
        *   `ufw allow 'OpenSSH'`: Mengizinkan lalu lintas masuk pada port 22 (SSH). Ini sangat penting agar Siswa tidak terkunci dari VM Siswa.

3.  **Aktifkan UFW:**
    Jika UFW belum aktif, aktifkan sekarang. Siswa akan diminta konfirmasi.
    ```bash
    sudo ufw enable
    ```
    *   **Output yang Diharapkan:**
        ```
        Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
        Firewall enabled and active on system startup
        ```
        Ketik `y` dan tekan `Enter`.

4.  **Verifikasi Aturan UFW:**
    Periksa status UFW untuk memastikan aturan yang Siswa tambahkan sudah aktif.
    ```bash
    sudo ufw status verbose
    ```
    *   **Output yang Diharapkan:**
        Siswa akan melihat daftar aturan yang diizinkan, termasuk Nginx HTTP, Nginx HTTPS, dan OpenSSH.
        ```
        Status: active
        Logging: on (low)
        Default: deny (incoming), allow (outgoing), disabled (routed)
        New profiles: skip

        To                         Action      From
        --                         ------      ----
        80/tcp (Nginx HTTP)        ALLOW       Anywhere
        443/tcp (Nginx HTTPS)      ALLOW       Anywhere
        22/tcp (OpenSSH)           ALLOW       Anywhere
        80/tcp (Nginx HTTP (v6))   ALLOW       Anywhere (v6)
        443/tcp (Nginx HTTPS (v6)) ALLOW       Anywhere (v6)
        22/tcp (OpenSSH (v6))      ALLOW       Anywhere (v6)
        ```

### 4.4. Membuat Halaman Web Sederhana

Nginx menyajikan file web dari direktori `/var/www/html` secara *default*. Mari kita buat halaman `index.html` sederhana di sana.

1.  **Buka File `index.html` dengan Nano:**
    ```bash
    sudo nano /var/www/html/index.html
    ```
    *   **Penjelasan:**
        *   `sudo`: Diperlukan karena direktori `/var/www/html` dimiliki oleh *root*.
        *   `nano`: Editor teks berbasis terminal yang mudah digunakan. Jika file `index.html` belum ada, Nano akan membuatnya.

2.  **Masukkan Konten HTML:**
    Salin dan tempel kode HTML berikut ke dalam editor Nano.
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>Server Web Pribadi Saya</title>
        <style>
            body { font-family: Arial, sans-serif; text-align: center; margin-top: 50px; }
            h1 { color: #333; }
            p { color: #666; }
        </style>
    </head>
    <body>
        <h1>Halo dari Server Web Pribadi Saya!</h1>
        <p>Ini adalah proyek berbasis pembelajaran Linux, Networking, dan Cloud Computing.</p>
        <p>Server ini berjalan di VM Linux di cloud menggunakan Nginx.</p>
    </body>
    </html>
    ```

3.  **Simpan dan Keluar dari Nano:**
    *   Tekan `Ctrl + O` (Write Out) untuk menyimpan. Nano akan meminta konfirmasi nama file, tekan `Enter`.
    *   Tekan `Ctrl + X` untuk keluar dari editor Nano.

### 4.5. Uji Server Web (dari VM)

Sebelum mencoba mengakses dari luar, mari kita pastikan server web berfungsi dengan baik dari dalam VM itu sendiri.

1.  **Gunakan `curl` untuk Menguji Server Lokal:**
    ```bash
    curl http://localhost
    ```
    *   **Penjelasan:**
        *   `curl`: Alat baris perintah untuk mentransfer data dengan URL.
        *   `http://localhost`: Mengacu pada server web yang berjalan di mesin yang sama (VM Siswa) melalui protokol HTTP.

    *   **Output yang Diharapkan:**
        Siswa seharusnya melihat seluruh kode HTML yang baru saja Siswa masukkan ke dalam file `index.html` ditampilkan di terminal Siswa. Ini menSiswakan bahwa Nginx berhasil menyajikan halaman tersebut.

## Langkah 5: Konfigurasi Jaringan dan Keamanan Cloud

Pada Langkah 2, Siswa sudah mengkonfigurasi *Security Group* atau aturan *firewall* di konsol cloud. Ini adalah bagian penting dari keamanan jaringan di cloud.

*   **Verifikasi Aturan:** Kembali ke konsol cloud Siswa dan pastikan *Security Group* (AWS/Azure) atau aturan *firewall* (GCP) yang terkait dengan VM Siswa mengizinkan lalu lintas masuk pada:
    *   **Port 22 (SSH):** Sumber IP Siswa saja (terbaik) atau `0.0.0.0/0`.
    *   **Port 80 (HTTP):** Sumber `0.0.0.0/0`.
    *   **Port 443 (HTTPS):** Sumber `0.0.0.0/0` (jika Siswa berencana mengimplementasikan HTTPS nanti).

*   **Peran IP Publik dan Privat:**
    *   VM Siswa memiliki **IP Privat** (misalnya, `172.31.x.x` atau `10.x.x.x`) yang digunakan untuk komunikasi internal dalam jaringan virtual cloud Siswa.
    *   VM Siswa juga memiliki **IP Publik** (misalnya, `3.x.x.x` atau `34.x.x.x`) yang digunakan untuk komunikasi dengan internet. Lalu lintas dari internet akan melewati IP publik ini dan di-*NAT* ke IP privat VM Siswa.

## Langkah 6: Pengaturan DNS 

Menggunakan nama domain akan membuat server Siswa lebih mudah diakses dan diingat.

1.  **Dapatkan Nama Domain:** Jika Siswa belum punya, Siswa bisa mendaftarkan nama domain dari penyedia domain (misalnya, Namecheap, GoDaddy). Ada juga layanan DNS gratis seperti Freenom (meskipun ketersediaannya bisa bervariasi).
2.  **Konfigurasi Catatan A:**
    *   Login ke panel kontrol penyedia domain Siswa atau layanan DNS yang Siswa gunakan.
    *   Cari bagian "DNS Management" atau "Zone File Editor".
    *   Buat catatan `A` baru:
        *   **Host/Name:** `@` (untuk domain utama Siswa, misalnya `namadomainSiswa.com`) atau `www` (untuk `www.namadomainSiswa.com`).
        *   **Value/Points to:** Masukkan **Alamat IP Publik** VM Siswa.
        *   **TTL (Time To Live):** Biarkan *default* (misalnya, 3600 detik).
    *   Simpan perubahan. Perubahan DNS mungkin memerlukan waktu beberapa menit hingga beberapa jam untuk menyebar ke seluruh internet (propagasi DNS).

## Langkah 7: Pengujian dan Verifikasi

Sekarang saatnya menguji apakah server web Siswa dapat diakses dari luar.

1.  **Akses dari Web Browser:**
    *   Buka *web browser* di komputer lokal Siswa (bukan di VM).
    *   Ketikkan **Alamat IP Publik VM Siswa** atau **Nama Domain Siswa** (jika sudah dikonfigurasi DNS dan propagasi selesai) di bilah alamat.
    *   Siswa seharusnya melihat halaman "Halo dari Server Web Pribadi Saya!" yang Siswa buat.

2.  **Verifikasi dengan Alat Jaringan Lokal:**
    *   **`ping`:** Uji konektivitas dasar ke IP publik VM Siswa.
        ```bash
        ping your_vm_public_ip
        ```
    *   **`curl`:** Uji akses HTTP dari lokal.
        ```bash
        curl http://your_vm_public_ip
        # atau jika DNS sudah aktif
        curl http://yourdomain.com
        ```
    *   **`dig` (untuk DNS):** Jika Siswa mengkonfigurasi DNS, periksa apakah nama domain Siswa sudah menunjuk ke IP yang benar.
        ```bash
        dig yourdomain.com
        ```

3.  **Verifikasi dengan Alat Jaringan di VM (SSH ke VM Siswa):**
    *   **`netstat` atau `ss`:** Pastikan Nginx mendengarkan di port 80.
        ```bash
        sudo netstat -tuln | grep 80
        # atau
        sudo ss -tuln | grep 80
        ```
        Siswa seharusnya melihat baris yang menunjukkan Nginx mendengarkan di `0.0.0.0:80` atau `:::80`.
    *   **`ip a`:** Pastikan antarmuka jaringan VM Siswa memiliki alamat IP yang benar.
        ```bash
        ip a
        ```

**Selamat!** Siswa telah berhasil membangun server web pribadi di cloud, mengintegrasikan pengetahuan Siswa tentang Linux, Networking, dan Cloud Computing. Ini adalah fondasi yang kuat untuk proyek-proyek yang lebih kompleks di masa depan.

**Langkah Selanjutnya (Opsional):**
*   **HTTPS:** Implementasikan HTTPS menggunakan Let's Encrypt (sertifikat SSL/TLS gratis) untuk mengamankan komunikasi.
*   **Domain Kustom:** Gunakan nama domain kustom Siswa sendiri.
*   **Konten Dinamis:** Instal PHP, Python, atau Node.js untuk membuat aplikasi web dinamis.
*   **Database:** Tambahkan database seperti MySQL atau PostgreSQL.
*   **Monitoring:** Konfigurasi alat monitoring untuk melacak kinerja server Siswa.
[[01_Dasar_Dasar_Linux]]
[[02_Konsep_Jaringan]]
[[03_Dasar_Dasar_Cloud_Computing]]