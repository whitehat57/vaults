# Modul 3: Dasar-dasar Cloud Computing

## Pengenalan Cloud Computing

### Definisi dan Karakteristik Utama

Cloud Computing adalah model pengiriman layanan komputasi—termasuk server, penyimpanan, database, jaringan, perangkat lunak, analitik, dan intelijen—melalui internet ("cloud"). Daripada memiliki dan memelihara infrastruktur komputasi Anda sendiri, Anda dapat mengakses layanan ini dari penyedia cloud seperti AWS, Google Cloud, atau Azure.

**Karakteristik Utama (NIST Definition):**

*   **On-demand self-service:** Pengguna dapat menyediakan sumber daya komputasi (misalnya, waktu server, penyimpanan jaringan) secara unilateral dan otomatis tanpa interaksi manusia dengan setiap penyedia layanan.
*   **Broad network access:** Kapabilitas tersedia melalui jaringan dan diakses melalui mekanisme standar yang mempromosikan penggunaan oleh platform klien tipis atau tebal (misalnya, ponsel, laptop, workstation).
*   **Resource pooling:** Sumber daya komputasi penyedia dikumpulkan untuk melayani banyak konsumen menggunakan model multi-tenant, dengan sumber daya fisik dan virtual yang berbeda secara dinamis dialokasikan dan dialokasikan kembali sesuai permintaan konsumen.
*   **Rapid elasticity:** Kapabilitas dapat disediakan dan dilepaskan secara elastis, dalam beberapa kasus secara otomatis, untuk menskalakan dengan cepat ke atas dan ke bawah sesuai permintaan. Bagi konsumen, kapabilitas yang tersedia untuk penyediaan seringkali tampak tidak terbatas dan dapat dibeli dalam jumlah berapa pun kapan saja.
*   **Measured service:** Sistem cloud secara otomatis mengontrol dan mengoptimalkan penggunaan sumber daya dengan memanfaatkan kemampuan pengukuran pada beberapa tingkat abstraksi yang sesuai dengan jenis layanan (misalnya, penyimpanan, pemrosesan, bandwidth, dan akun pengguna aktif). Penggunaan sumber daya dapat dipantau, dikontrol, dan dilaporkan, memberikan transparansi bagi penyedia dan konsumen layanan yang digunakan.

### Manfaat dan Tantangan Cloud Computing

**Manfaat:**

*   **Skalabilitas:** Kemampuan untuk dengan cepat menambah atau mengurangi sumber daya sesuai kebutuhan.
*   **Fleksibilitas:** Pilihan layanan yang luas dan kemampuan untuk memilih teknologi yang paling sesuai.
*   **Efisiensi Biaya:** Beralih dari model CAPEX (Capital Expenditure) ke OPEX (Operational Expenditure), hanya membayar untuk apa yang digunakan. Mengurangi kebutuhan investasi awal pada perangkat keras.
*   **Keandalan dan Ketersediaan Tinggi:** Penyedia cloud menawarkan infrastruktur yang redundan dan terdistribusi secara geografis untuk memastikan ketersediaan layanan yang tinggi.
*   **Keamanan:** Penyedia cloud menginvestasikan sumber daya besar dalam keamanan fisik dan siber, seringkali melebihi kemampuan organisasi individu. Namun, keamanan adalah tanggung jawab bersama.
*   **Fokus pada Inovasi:** Tim IT dapat fokus pada pengembangan aplikasi dan inovasi bisnis daripada mengelola infrastruktur.

**Tantangan:**

*   **Ketergantungan Vendor:** Sulit untuk berpindah antar penyedia cloud (vendor lock-in).
*   **Keamanan Data:** Meskipun penyedia cloud aman, tanggung jawab pengguna untuk mengamankan data mereka sendiri.
*   **Biaya yang Tidak Terduga:** Jika tidak dikelola dengan baik, biaya cloud bisa membengkak.
*   **Kepatuhan Regulasi:** Memastikan data mematuhi peraturan lokal dan internasional bisa menjadi kompleks.
*   **Konektivitas Jaringan:** Kinerja aplikasi cloud sangat bergantung pada koneksi internet yang stabil dan cepat.

## Model Layanan Cloud

Model layanan cloud mendefinisikan tingkat kontrol yang dimiliki pengguna atas infrastruktur dan perangkat lunak.

*   **IaaS (Infrastructure as a Service):**
    *   **Definisi:** Menyediakan sumber daya komputasi dasar seperti mesin virtual (VM), penyimpanan, jaringan, dan sistem operasi. Pengguna memiliki kontrol penuh atas OS, aplikasi, dan data.
    *   **Contoh:** Amazon EC2, Google Compute Engine, Azure Virtual Machines.
    *   **Penggunaan:** Cocok untuk migrasi aplikasi *on-premise*, pengembangan dan pengujian, serta *hosting* situs web.
    *   **Keterkaitan:** Di IaaS, Anda akan sering berinteraksi langsung dengan VM Linux, menginstal perangkat lunak, mengkonfigurasi jaringan, dan menerapkan *shell script* untuk otomatisasi, sama seperti server fisik.

*   **PaaS (Platform as a Service):**
    *   **Definisi:** Menyediakan lingkungan *runtime* yang lengkap untuk mengembangkan, menjalankan, dan mengelola aplikasi tanpa kompleksitas membangun dan memelihara infrastruktur. Pengguna fokus pada kode aplikasi.
    *   **Contoh:** Google App Engine, AWS Elastic Beanstalk, Heroku.
    *   **Penggunaan:** Pengembangan aplikasi web, API, dan layanan mikro.
    *   **Keterkaitan:** Meskipun Anda tidak mengelola OS secara langsung, aplikasi Anda yang berjalan di PaaS akan sering berinteraksi dengan layanan jaringan dan mungkin menggunakan alat-alat yang dibangun di atas Linux di bawahnya.

*   **SaaS (Software as a Service):**
    *   **Definisi:** Menyediakan aplikasi perangkat lunak yang siap digunakan melalui internet. Pengguna hanya perlu mengakses aplikasi melalui *web browser* atau klien.
    *   **Contoh:** Gmail, Salesforce, Microsoft 365, Dropbox.
    *   **Penggunaan:** Aplikasi bisnis, kolaborasi, penyimpanan file.
    *   **Keterkaitan:** Pengguna tidak memiliki kontrol atas infrastruktur atau platform. Ini adalah layanan yang paling abstrak dari sudut pandang pengguna.

## Model Penyebaran Cloud

Model penyebaran cloud mendefinisikan lokasi dan kepemilikan infrastruktur cloud.

*   **Public Cloud:**
    *   **Definisi:** Layanan cloud disediakan oleh penyedia pihak ketiga dan tersedia untuk umum melalui internet. Infrastruktur dimiliki dan dioperasikan oleh penyedia cloud.
    *   **Contoh:** AWS, Google Cloud, Microsoft Azure.
    *   **Manfaat:** Skalabilitas tinggi, biaya rendah, tanpa pemeliharaan infrastruktur.
*   **Private Cloud:**
    *   **Definisi:** Infrastruktur cloud dioperasikan secara eksklusif untuk satu organisasi. Dapat dikelola secara internal atau oleh pihak ketiga.
    *   **Contoh:** Infrastruktur cloud yang dibangun di pusat data perusahaan.
    *   **Manfaat:** Kontrol penuh atas keamanan dan data, kepatuhan regulasi yang lebih mudah.
*   **Hybrid Cloud:**
    *   **Definisi:** Kombinasi dari dua atau lebih jenis cloud (misalnya, privat dan publik) yang tetap merupakan entitas unik tetapi terikat bersama oleh teknologi yang memungkinkan portabilitas data dan aplikasi.
    *   **Contoh:** Menggunakan *private cloud* untuk data sensitif dan *public cloud* untuk aplikasi web yang menghadap publik.
    *   **Manfaat:** Fleksibilitas, optimasi biaya, memanfaatkan kekuatan kedua model.
*   **Community Cloud:**
    *   **Definisi:** Infrastruktur cloud dibagi oleh beberapa organisasi dengan kekhawatiran bersama (misalnya, misi, persyaratan keamanan, kebijakan, dan pertimbangan kepatuhan).
    *   **Contoh:** Cloud untuk lembaga pemerintah atau penelitian.

## Penyedia Layanan Cloud Utama

*   **Amazon Web Services (AWS):**
    *   Penyedia cloud terbesar dan paling matang, menawarkan lebih dari 200 layanan.
    *   Layanan populer: EC2 (VM), S3 (penyimpanan objek), Lambda (serverless functions), VPC (jaringan virtual).
*   **Microsoft Azure:**
    *   Penyedia cloud terbesar kedua, terintegrasi erat dengan produk Microsoft.
    *   Layanan populer: Azure Virtual Machines, Azure Blob Storage, Azure Functions, Azure Virtual Network.
*   **Google Cloud Platform (GCP):**
    *   Dikenal karena kekuatan dalam data analitik, *machine learning*, dan kontainer.
    *   Layanan populer: Compute Engine (VM), Cloud Storage, Google Kubernetes Engine (GKE), Cloud Functions.

## Konsep Virtualisasi

Virtualisasi adalah teknologi yang memungkinkan pembuatan versi virtual dari sumber daya komputasi, seperti sistem operasi, server, perangkat penyimpanan, atau sumber daya jaringan.

### Apa itu Virtualisasi?

Virtualisasi menciptakan lapisan abstraksi antara perangkat keras fisik dan perangkat lunak yang berjalan di atasnya. Ini memungkinkan satu server fisik untuk menjalankan beberapa sistem operasi atau aplikasi secara bersamaan, masing-masing dalam lingkungan virtualnya sendiri.

### Mesin Virtual (VM) dan Hypervisor

*   **Mesin Virtual (VM):**
    *   Lingkungan komputasi yang terisolasi dan mandiri yang meniru sistem komputer fisik.
    *   Setiap VM memiliki sistem operasi (OS) tamu dan aplikasi sendiri, serta sumber daya virtual (CPU, RAM, penyimpanan, jaringan) yang dialokasikan dari *host* fisik.
    *   VM sepenuhnya terisolasi satu sama lain, sehingga masalah di satu VM tidak memengaruhi yang lain.
*   **Hypervisor (Virtual Machine Monitor - VMM):**
    *   Perangkat lunak, *firmware*, atau perangkat keras yang membuat dan menjalankan mesin virtual.
    *   **Type 1 (Bare-metal) Hypervisor:** Berjalan langsung di atas perangkat keras fisik (misalnya, VMware ESXi, Microsoft Hyper-V, KVM). Sangat efisien dan aman.
    *   **Type 2 (Hosted) Hypervisor:** Berjalan di atas sistem operasi *host* (misalnya, Oracle VirtualBox, VMware Workstation). Lebih mudah diatur untuk penggunaan desktop, tetapi memiliki *overhead* kinerja.

**Keterkaitan dengan Linux:**
KVM (Kernel-based Virtual Machine) adalah hypervisor Type 1 yang terintegrasi ke dalam kernel Linux, menjadikannya pilihan populer untuk virtualisasi di server Linux dan di banyak penyedia cloud. Memahami VM dan hypervisor adalah dasar untuk memahami bagaimana server di cloud beroperasi.

## Dasar-dasar Kontainerisasi

Kontainerisasi adalah bentuk virtualisasi ringan yang memungkinkan aplikasi dan semua dependensinya dikemas bersama dalam unit yang terisolasi.

### Pengenalan Docker (Konsep Image, Container)

*   **Docker:** Platform *open-source* paling populer untuk mengembangkan, mengirim, dan menjalankan aplikasi menggunakan teknologi kontainer.
*   **Image Docker:**
    *   Template *read-only* yang berisi aplikasi, kode, *runtime*, pustaka, variabel lingkungan, dan file konfigurasi yang diperlukan untuk menjalankan aplikasi.
    *   Mirip dengan "cetak biru" atau "snapshot" dari aplikasi.
*   **Container Docker:**
    *   Instansi *runtime* dari sebuah *image* Docker.
    *   Lingkungan yang terisolasi dan portabel di mana aplikasi berjalan.
    *   Dapat dimulai, dihentikan, dipindahkan, dan dihapus dengan mudah.

### Perbedaan antara VM dan Kontainer

| Fitur           | Mesin Virtual (VM)                      | Kontainer                                  |
| :-------------- | :-------------------------------------- | :----------------------------------------- |
| Abstraksi       | Abstraksi perangkat keras               | Abstraksi tingkat OS                       |
| OS              | Setiap VM memiliki OS tamu sendiri      | Berbagi kernel OS *host*                   |
| Ukuran          | Lebih besar (GB)                        | Lebih kecil (MB)                           |
| Waktu Boot      | Menit                                   | Detik                                      |
| Isolasi         | Isolasi yang kuat (tingkat OS)          | Isolasi yang lebih ringan (tingkat proses) |
| Portabilitas    | Kurang portabel (membutuhkan hypervisor) | Sangat portabel (berjalan di mana saja dengan Docker) |
| Overhead        | Lebih tinggi (karena OS tamu penuh)     | Lebih rendah                               |

**Keterkaitan dengan Linux:**
Kontainer (termasuk Docker) sangat bergantung pada fitur-fitur kernel Linux seperti `cgroups` (untuk manajemen sumber daya) dan `namespaces` (untuk isolasi proses). Sebagian besar kontainer berjalan di atas *host* Linux, dan banyak aplikasi cloud-native modern dibangun menggunakan kontainer. Memahami Docker dan kontainer adalah keterampilan penting untuk *deployment* aplikasi di cloud.

## Pertimbangan Keamanan Cloud

Keamanan di cloud adalah tanggung jawab bersama antara penyedia cloud dan pengguna.

### Tanggung Jawab Bersama (Shared Responsibility Model)

*   **Penyedia Cloud (misalnya, AWS, Azure, GCP):** Bertanggung jawab atas **keamanan *dari* cloud** (Security *of* the Cloud). Ini mencakup keamanan infrastruktur fisik, jaringan, komputasi, penyimpanan, dan database yang mendasari layanan cloud.
*   **Pengguna Cloud:** Bertanggung jawab atas **keamanan *di dalam* cloud** (Security *in* the Cloud). Ini mencakup:
    *   Data Anda (enkripsi, kontrol akses).
    *   Konfigurasi jaringan (firewall, *security groups*).
    *   Manajemen identitas dan akses (IAM).
    *   Sistem operasi tamu (patching, konfigurasi).
    *   Aplikasi yang Anda *deploy*.

### Ancaman Umum di Cloud

*   **Konfigurasi yang Salah:** Kesalahan dalam pengaturan *security groups*, izin IAM, atau konfigurasi penyimpanan yang membuat sumber daya terekspos.
*   **Manajemen Identitas dan Akses yang Buruk:** Kredensial yang lemah, izin yang terlalu luas, atau tidak menggunakan MFA (Multi-Factor Authentication).
*   **API yang Tidak Aman:** Kerentanan dalam API cloud yang diekspos.
*   **Pembajakan Akun:** Penyerang mendapatkan akses ke akun cloud Anda.
*   **Ancaman Internal:** Karyawan yang tidak puas atau lalai.
*   **DDoS (Distributed Denial of Service):** Serangan yang membanjiri sumber daya cloud untuk membuatnya tidak tersedia.
*   **Malware dan Ransomware:** Perangkat lunak berbahaya yang menginfeksi instance cloud.

**Keterkaitan dengan Linux dan Networking:**
Pengetahuan tentang keamanan Linux (izin file, manajemen pengguna, firewall) dan konsep jaringan (subnetting, protokol, firewall) sangat penting untuk memenuhi bagian "keamanan *di dalam* cloud" dari model tanggung jawab bersama. Mengamankan VM Linux, mengkonfigurasi *security groups* jaringan virtual, dan memantau lalu lintas adalah tugas-tugas yang membutuhkan pemahaman mendalam tentang ketiga domain ini.

[[01_Dasar_Dasar_Linux]]
[[02_Konsep_Jaringan]]
[[04_Project_Based_Learning]]