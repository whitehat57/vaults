# Modul 2: Konsep Jaringan (Networking)

## Model OSI dan TCP/IP

Memahami bagaimana data bergerak melalui jaringan adalah fundamental. Dua model referensi utama yang menjelaskan proses ini adalah Model OSI (Open Systems Interconnection) dan Model TCP/IP.

### Model OSI (Open Systems Interconnection)

Model OSI adalah kerangka kerja konseptual yang menstandarisasi fungsi sistem komunikasi menjadi tujuh lapisan abstrak. Tujuannya adalah untuk memungkinkan interoperabilitas antara berbagai produk dan perangkat lunak dari vendor yang berbeda.

*   **Lapisan 7: Application Layer (Aplikasi)**
    *   Menyediakan antarmuka untuk aplikasi pengguna. Contoh: HTTP, FTP, SMTP, DNS.
*   **Lapisan 6: Presentation Layer (Presentasi)**
    *   Bertanggung jawab untuk format data, enkripsi, dan kompresi. Contoh: JPEG, MPEG, ASCII.
*   **Lapisan 5: Session Layer (Sesi)**
    *   Mengelola sesi komunikasi antara aplikasi. Contoh: NetBIOS, RPC.
*   **Lapisan 4: Transport Layer (Transportasi)**
    *   Menyediakan komunikasi *end-to-end* yang andal atau tidak andal. Contoh: TCP (Transmission Control Protocol), UDP (User Datagram Protocol).
*   **Lapisan 3: Network Layer (Jaringan)**
    *   Bertanggung jawab untuk pengalamatan logis (IP address) dan *routing* paket antar jaringan. Contoh: IP (Internet Protocol), ICMP.
*   **Lapisan 2: Data Link Layer (Data Link)**
    *   Menyediakan transfer data yang andal antara dua node yang terhubung langsung. Menggunakan alamat fisik (MAC address). Contoh: Ethernet, PPP.
*   **Lapisan 1: Physical Layer (Fisik)**
    *   Menentukan spesifikasi fisik untuk transmisi data (kabel, sinyal listrik, gelombang radio). Contoh: Kabel UTP, serat optik, Wi-Fi.

### Model TCP/IP

Model TCP/IP adalah model yang lebih praktis dan banyak digunakan dalam implementasi jaringan modern (terutama internet). Ini adalah model empat lapisan yang menggabungkan beberapa lapisan OSI.

*   **Lapisan 4: Application Layer (Aplikasi)**
    *   Menggabungkan lapisan Aplikasi, Presentasi, dan Sesi dari model OSI. Contoh: HTTP, FTP, DNS, SMTP.
*   **Lapisan 3: Transport Layer (Transportasi)**
    *   Sama dengan lapisan Transportasi di OSI. Contoh: TCP, UDP.
*   **Lapisan 2: Internet Layer (Internet)**
    *   Sama dengan lapisan Jaringan di OSI. Bertanggung jawab untuk pengalamatan dan *routing*. Contoh: IP, ICMP, ARP.
*   **Lapisan 1: Network Access Layer (Akses Jaringan)**
    *   Menggabungkan lapisan Data Link dan Fisik dari model OSI. Bertanggung jawab untuk detail perangkat keras dan transmisi data fisik. Contoh: Ethernet, Wi-Fi.

### Perbandingan Kedua Model

| Fitur           | Model OSI                               | Model TCP/IP                               |
| :-------------- | :-------------------------------------- | :----------------------------------------- |
| Lapisan         | 7 Lapisan                               | 4 Lapisan                                  |
| Pendekatan      | Konseptual, teoritis                    | Praktis, implementasi nyata                |
| Pengembangan    | Dikembangkan oleh ISO                   | Dikembangkan oleh DoD (Departemen Pertahanan AS) |
| Fokus           | Layanan, antarmuka, protokol            | Protokol                                   |
| Fleksibilitas   | Kurang fleksibel (ketat)                | Lebih fleksibel                            |
| Penggunaan      | Referensi, pendidikan                   | Implementasi internet                      |

**Keterkaitan dengan Linux:**
Linux mengimplementasikan model TCP/IP secara ekstensif. Setiap lapisan model ini memiliki representasi dalam kernel Linux dan utilitas baris perintah. Misalnya, konfigurasi antarmuka jaringan (Lapisan Akses Jaringan), pengaturan alamat IP dan *routing* (Lapisan Internet), serta manajemen *socket* TCP/UDP (Lapisan Transportasi) semuanya dilakukan melalui perintah Linux.

## Pengalamatan IP

Pengalamatan IP adalah cara perangkat di jaringan diidentifikasi dan berkomunikasi satu sama lain.

### IPv4 dan IPv6

*   **IPv4 (Internet Protocol version 4):**
    *   Format: Empat set angka desimal, dipisahkan oleh titik (misalnya, `192.168.1.1`).
    *   Ukuran: 32-bit.
    *   Jumlah Alamat: Sekitar 4,3 miliar alamat unik. Keterbatasan ini menyebabkan munculnya IPv6.
*   **IPv6 (Internet Protocol version 6):**
    *   Format: Delapan kelompok empat digit heksadesimal, dipisahkan oleh titik dua (misalnya, `2001:0db8:85a3:0000:0000:8a2e:0370:7334`).
    *   Ukuran: 128-bit.
    *   Jumlah Alamat: Sangat besar (sekitar 340 undecillion), mengatasi masalah kelangkaan alamat IPv4.
    *   Fitur Tambahan: Keamanan bawaan (IPsec), konfigurasi otomatis, *routing* yang lebih efisien.

### Konsep Subnetting dan CIDR

*   **Subnetting:** Proses membagi jaringan IP besar menjadi sub-jaringan yang lebih kecil (subnet). Ini membantu dalam:
    *   Efisiensi penggunaan alamat IP.
    *   Mengurangi *broadcast domain*.
    *   Meningkatkan keamanan dan kinerja jaringan.
    *   Setiap subnet memiliki alamat jaringan, *broadcast address*, dan rentang alamat *host* yang valid.
*   **CIDR (Classless Inter-Domain Routing):**
    *   Metode untuk mengalokasikan alamat IP dan *routing* paket IP.
    *   Menggantikan sistem kelas (A, B, C) yang kurang efisien.
    *   Menggunakan notasi `/prefix-length` (misalnya, `192.168.1.0/24`), di mana `prefix-length` menunjukkan jumlah bit yang digunakan untuk bagian jaringan dari alamat IP.
    *   Contoh: `/24` berarti 24 bit pertama adalah bagian jaringan, dan 8 bit sisanya adalah bagian *host*.

### Alamat IP Publik dan Privat

*   **Alamat IP Publik:**
    *   Alamat yang dapat diakses secara langsung dari internet.
    *   Unik secara global.
    *   Digunakan oleh *router* dan server yang terhubung langsung ke internet.
*   **Alamat IP Privat:**
    *   Alamat yang hanya dapat diakses dalam jaringan lokal (LAN).
    *   Tidak dapat di-*routing* langsung di internet.
    *   Rentang alamat privat yang umum:
        *   `10.0.0.0` - `10.255.255.255` (Kelas A)
        *   `172.16.0.0` - `172.31.255.255` (Kelas B)
        *   `192.168.0.0` - `192.168.255.255` (Kelas C)
    *   Perangkat di jaringan privat menggunakan NAT (Network Address Translation) untuk berkomunikasi dengan internet menggunakan satu atau beberapa alamat IP publik.

**Keterkaitan dengan Linux:**
Di Linux, Anda dapat mengkonfigurasi alamat IP, *netmask*, dan *gateway* menggunakan perintah seperti `ip address` atau `ifconfig` (lama). Pengetahuan tentang subnetting dan CIDR sangat penting saat mengkonfigurasi antarmuka jaringan di server Linux, baik fisik maupun virtual di cloud.

## Protokol Jaringan Penting

Protokol adalah seperangkat aturan yang mengatur bagaimana data diformat, ditransmisikan, dan diterima.

*   **HTTP (Hypertext Transfer Protocol) / HTTPS (HTTP Secure):**
    *   **Fungsi:** Protokol dasar untuk World Wide Web, digunakan untuk mentransfer halaman web dan data lainnya.
    *   **Port:** HTTP menggunakan port 80, HTTPS menggunakan port 443.
    *   **HTTPS:** Versi aman dari HTTP yang menggunakan SSL/TLS untuk enkripsi komunikasi, melindungi privasi dan integritas data.
*   **DNS (Domain Name System):**
    *   **Fungsi:** Menerjemahkan nama domain yang mudah diingat (misalnya, `google.com`) menjadi alamat IP numerik yang digunakan oleh komputer.
    *   **Port:** UDP/TCP port 53.
    *   **Pentingnya:** Tanpa DNS, kita harus mengingat alamat IP setiap situs web yang ingin kita kunjungi.
*   **DHCP (Dynamic Host Configuration Protocol):**
    *   **Fungsi:** Secara otomatis menetapkan alamat IP, *subnet mask*, *default gateway*, dan server DNS kepada perangkat di jaringan.
    *   **Port:** UDP port 67 (server) dan 68 (klien).
    *   **Manfaat:** Menyederhanakan administrasi jaringan dan mencegah konflik alamat IP.
*   **SSH (Secure Shell):**
    *   **Fungsi:** Protokol jaringan kriptografi untuk operasi layanan jaringan yang aman melalui jaringan yang tidak aman. Paling sering digunakan untuk akses *remote command-line* ke server Linux.
    *   **Port:** TCP port 22.
    *   **Keamanan:** Mengenkripsi semua lalu lintas antara klien dan server, termasuk kata sandi.
*   **FTP (File Transfer Protocol) / SFTP (SSH File Transfer Protocol):**
    *   **Fungsi:**
        *   **FTP:** Protokol standar untuk mentransfer file antara komputer di jaringan. Tidak aman karena tidak mengenkripsi data.
        *   **SFTP:** Protokol transfer file yang aman yang berjalan di atas SSH. Mengenkripsi data dan kredensial.
    *   **Port:** FTP menggunakan TCP port 20 (data) dan 21 (kontrol). SFTP menggunakan TCP port 22 (melalui SSH).

**Keterkaitan dengan Linux:**
Linux adalah platform utama untuk menjalankan server yang menggunakan protokol-protokol ini (misalnya, server web Apache/Nginx untuk HTTP/HTTPS, BIND untuk DNS, OpenSSH untuk SSH/SFTP). Memahami protokol ini sangat penting untuk mengkonfigurasi layanan jaringan di Linux dan memecahkan masalah konektivitas.

## Alat Troubleshooting Jaringan

Alat baris perintah di Linux sangat efektif untuk mendiagnosis masalah jaringan.

*   `ping`:
    *   **Fungsi:** Menguji konektivitas jaringan ke *host* lain dan mengukur waktu *round-trip* untuk paket. Menggunakan protokol ICMP.
    *   **Penggunaan:** `ping alamat_ip_atau_domain`
    ```bash
    ping google.com
    ping 192.168.1.1
    ```
*   `traceroute` (atau `tracert` di Windows):
    *   **Fungsi:** Melacak jalur (rute) yang diambil paket dari sumber ke tujuan, menampilkan setiap *router* (hop) di sepanjang jalan.
    *   **Penggunaan:** `traceroute alamat_ip_atau_domain`
    ```bash
    traceroute google.com
    ```
*   `netstat` (Network Statistics):
    *   **Fungsi:** Menampilkan koneksi jaringan aktif, tabel *routing*, statistik antarmuka, koneksi *masquerade*, dan keanggotaan *multicast*.
    *   **Penggunaan Umum:**
        *   `netstat -tuln`: Menampilkan semua *listening* TCP (`t`) dan UDP (`u`) *socket* dalam format numerik (`n`).
        *   `netstat -r`: Menampilkan tabel *routing*.
    ```bash
    netstat -tuln
    # Output contoh:
    # Proto Recv-Q Send-Q Local Address           Foreign Address         State
    # tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
    # tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
    ```
*   `ip a` (ip address):
    *   **Fungsi:** Menampilkan alamat IP, *netmask*, dan informasi antarmuka jaringan lainnya. Ini adalah pengganti modern untuk `ifconfig`.
    *   **Penggunaan:** `ip a` atau `ip addr show`
    ```bash
    ip a
    # Output contoh:
    # 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    #     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    #     inet 127.0.0.1/8 scope host lo
    #        valid_lft forever preferred_lft forever
    # 2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    #     link/ether 00:0c:29:12:34:56 brd ff:ff:ff:ff:ff:ff
    #     inet 192.168.1.100/24 brd 192.168.1.255 scope global dynamic eth0
    #        valid_lft 86399sec preferred_lft 86399sec
    ```
*   `ss` (Socket Statistics):
    *   **Fungsi:** Alat yang lebih cepat dan lebih informatif daripada `netstat` untuk menampilkan informasi *socket*.
    *   **Penggunaan Umum:**
        *   `ss -tuln`: Menampilkan *listening* TCP dan UDP *socket*.
        *   `ss -s`: Menampilkan ringkasan statistik *socket*.
    ```bash
    ss -tuln
    ```
*   `dig` (Domain Information Groper) / `nslookup`:
    *   **Fungsi:** Mengkueri server DNS untuk mendapatkan informasi tentang nama domain, alamat IP, dan catatan DNS lainnya.
    *   **Penggunaan:** `dig nama_domain` atau `nslookup nama_domain`
    ```bash
    dig google.com
    ```

### Analisis Dasar Output Alat

*   **`ping`:** Jika ada balasan, konektivitas dasar ada. Jika tidak, ada masalah di sepanjang jalur. Waktu RTT (Round Trip Time) menunjukkan latensi.
*   **`traceroute`:** Menunjukkan di mana paket berhenti atau melambat, membantu mengidentifikasi *router* yang bermasalah.
*   **`netstat`/`ss`:** Membantu melihat port mana yang terbuka dan layanan apa yang sedang berjalan, serta koneksi aktif. Ini penting untuk *troubleshooting* aplikasi yang tidak dapat diakses atau untuk memeriksa potensi kerentanan.
*   **`ip a`:** Memverifikasi konfigurasi IP lokal, termasuk alamat, *netmask*, dan status antarmuka.

**Keterkaitan dengan Linux dan Cybersecurity:**
Alat-alat ini adalah bagian integral dari *toolkit* setiap administrator Linux dan profesional *cybersecurity*. Mereka digunakan untuk memverifikasi konfigurasi jaringan, mendiagnosis masalah konektivitas, dan melakukan *reconnaissance* (pengintaian) pada sistem target untuk mengidentifikasi port terbuka atau layanan yang berjalan.

## Konsep Firewall

Firewall adalah sistem keamanan jaringan yang memantau dan mengontrol lalu lintas jaringan masuk dan keluar berdasarkan aturan keamanan yang telah ditentukan sebelumnya.

### Fungsi Firewall

*   **Penyaringan Paket:** Memeriksa header paket (alamat IP sumber/tujuan, port, protokol) dan memutuskan apakah akan mengizinkan atau memblokir paket.
*   **Kontrol Akses:** Membatasi akses ke atau dari jaringan atau sistem tertentu.
*   **Pencatatan (Logging):** Mencatat lalu lintas yang diizinkan atau diblokir untuk tujuan audit dan analisis keamanan.
*   **NAT (Network Address Translation):** Mengubah alamat IP privat menjadi alamat IP publik dan sebaliknya, memungkinkan banyak perangkat di jaringan privat berbagi satu alamat IP publik.

### Pengenalan Dasar `iptables` atau `ufw`

Di Linux, `iptables` adalah *utility* baris perintah yang digunakan untuk mengkonfigurasi tabel aturan *packet filtering* kernel Linux firewall (Netfilter). `ufw` (Uncomplicated Firewall) adalah antarmuka yang lebih mudah digunakan untuk `iptables`.

*   **`iptables`:**
    *   Sangat kuat dan fleksibel, tetapi kompleks.
    *   Aturan diatur dalam tabel (misalnya, `filter`, `nat`), rantai (misalnya, `INPUT`, `OUTPUT`, `FORWARD`), dan target (misalnya, `ACCEPT`, `DROP`, `REJECT`).
    *   Contoh:
        ```bash
        # Mengizinkan lalu lintas SSH masuk
        sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

        # Memblokir semua lalu lintas masuk lainnya
        sudo iptables -A INPUT -j DROP

        # Melihat aturan yang ada
        sudo iptables -L -n -v
        ```
*   **`ufw` (Uncomplicated Firewall):**
    *   Dirancang untuk menyederhanakan konfigurasi firewall.
    *   Sangat direkomendasikan untuk sebagian besar pengguna dan server Linux.
    *   Contoh:
        ```bash
        # Mengaktifkan ufw
        sudo ufw enable

        # Mengizinkan SSH
        sudo ufw allow ssh

        # Mengizinkan HTTP
        sudo ufw allow http

        # Mengizinkan HTTPS
        sudo ufw allow https

        # Melihat status firewall
        sudo ufw status verbose

        # Menolak semua lalu lintas masuk secara default (ini adalah default ufw)
        sudo ufw default deny incoming
        ```

**Keterkaitan dengan Cybersecurity dan Cloud Computing:**
Firewall adalah komponen keamanan jaringan yang sangat penting. Di Linux, mengkonfigurasi `iptables` atau `ufw` adalah langkah krusial untuk mengamankan server dari akses tidak sah. Di lingkungan cloud, konsep *security groups* atau *network access control lists* (NACLs) berfungsi mirip dengan firewall, mengontrol lalu lintas ke dan dari instance virtual Anda. Memahami prinsip firewall di Linux akan membantu Anda mengkonfigurasi keamanan jaringan di cloud dengan lebih baik.
[[01_Dasar_Dasar_Linux]]
[[03_Dasar_Dasar_Cloud_Computing]]