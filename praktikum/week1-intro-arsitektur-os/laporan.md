
# Laporan Praktikum Minggu [1]
Topik: Arsitekstur Sistem Operasi Dan Kernel

---

## Identitas
- **Nama**  : PRIMA RADITA PRATAMA
- **NIM**   : 250202960
- **Kelas** : 1IKRA 

---

## Tujuan
Memahami fungsi dasar sistem operasi dan kernel,memahami WSL untuk memahami Linux di Windows, dan mengidentifikasi micro kernel.

---

## Dasar Teori
Sistem Operasi(OS) adalah software yang mengatur seluruh aktifitas hardware dan software pada komputer. Sistem Operasi juga yang menghubungkan antara user dan hardware yang memungkinkan user berinteraksi dan menjalankan aplikasi. Salah satu bagian terpentingnya adalah Kernel, yaitu inti Sistem Operasi yang mengelola sumber daya seperti : CPU, Hardisk/SSD/Memori, dan perangkat I/O.

Linux merupakan sistem operasi berbasis kernel monolithic yang bersifat open source.
Windows Subsystem for Linux (WSL) adalah fitur bawaan windows yang memungkinkan pengguna menjalankan lingkungan Linux secara langsung di atas Windows tanpa perlu mesin virtual/dualboot. WSL dapat menerjemahkan systemcall Linux agar kompatibel dengan kernel Windows.
Percobaan ini bertujuan mengenal konsep kernel, sistem operasi berbasis Linux, serta memahami cara kerja WSL sebagai jembatan antara OS Windows dan Linux.

---

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.  
2. Perintah yang dijalankan.  
3. File dan kode yang dibuat.  
4. Commit message yang digunakan.

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
uname -a
lsmod | head
dmesg | head
```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)

---

## Analisis
- Jelaskan makna hasil percobaan.  
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  

---

## Kesimpulan
-nstalasi WSL berhasil menciptakan lingkungan kerja Linux di dalam Windows, sehingga user dapat menjalankan perintah dan aplikasi Linux secara langsung.
-Peran Kernel sebagai inti sistem operasi yang mengatur komunikasi antara hardware dan software, serta mengenali konsep system call dan arsitektur berlapis dalam sistem operasi.
-Meskipun WSL tidak menjalankan kernel Linux secara penuh seperti sistem Linux asli, hasil percobaan menunjukan bahwa hubungan antara Windows dan Linux melalui WSL tetap efisien dan fungsional untuk pengembangan maupun pembelajaran sistem operasi.


## Perbedaan Monolithic Kernel, Microkernel, dan Layered Architecture
Arsitektur sistem operasi merupakan fondasi penting yang menentukan bagaimana perangkat keras berinteraksi dengan perangkat lunak serta bagaimana layanan OS diberikan kepada aplikasi dan pengguna. Tiga model yang paling dikenal adalah monolithic kernel, microkernel, dan layered architecture.

## Monolithic Kernel
Monolithic kernel adalah arsitektur di mana semua layanan OS inti (manajemen proses, manajemen memori, file system, device drivers, networking, dll.) berjalan di ruang alamat kernel tunggal. Semua komponen ini saling berkomunikasi langsung dan berada pada tingkat privilese tertinggi. Karena semua bagian terintegrasi erat, mereka dapat berinteraksi dengan sangat efisien.

## Micro Kernel
Microkernel adalah pendekatan yang berusaha membuat kernel sesederhana mungkin. Hanya fungsi dasar seperti komunikasi antar-proses (IPC), manajemen memori sederhana, dan scheduling yang berjalan di kernel space. Layanan lain, termasuk driver perangkat dan sistem file, ditempatkan di user space. Kelebihan utamanya adalah keamanan, modularitas, dan keandalan: jika satu layanan gagal, sistem inti tetap berjalan. Namun, kelemahannya adalah overhead komunikasi (karena sering memerlukan mekanisme IPC) yang dapat menurunkan performa jika tidak dioptimalkan.

Contoh nyata: QNX, Minix, Mach (digunakan dalam varian macOS dan iOS).

## Layered Architecture
Layered architecture membagi sistem operasi ke dalam beberapa lapisan (layer) yang hierarkis, dari hardware di bawah hingga antarmuka pengguna di atas. Setiap lapisan hanya berinteraksi dengan lapisan di atas dan di bawahnya. Model ini menawarkan desain yang terstruktur dan mudah dipahami, sehingga lebih sederhana dalam pengembangan dan pemeliharaan. Kelemahannya adalah potensi penurunan efisiensi, karena kadang permintaan harus melewati beberapa lapisan meskipun sebenarnya bisa diakses lebih langsung.

## Analisis Relevansi Untuk Sistem Modern
Dalam konteks sistem modern, setiap model memiliki relevansi tersendiri tergantung kebutuhan:
- Monolithic kernel tetap populer, khususnya dalam sistem open source dan server (misalnya Linux). Alasannya, performa tinggi sangat dibutuhkan pada aplikasi berskala besar, dan komunitas mampu mengelola kompleksitas kode. Linux juga mendukung modularisasi (loadable kernel modules), sehingga sebagian kelemahan monolithic kernel bisa diatasi.
- Microkernel semakin relevan untuk sistem embedded dan real-time, di mana keandalan dan keamanan menjadi prioritas utama. Misalnya, QNX digunakan pada sistem otomotif dan peralatan industri. Namun, untuk desktop atau server umum, microkernel murni masih jarang dipakai karena trade-off performa.
- Layered architecture lebih dilihat sebagai konsep desain daripada implementasi murni. OS modern seperti Windows dan macOS tidak sepenuhnya layered, tetapi memanfaatkan struktur berlapis untuk menjaga modularitas dan keteraturan. Dengan demikian, layered architecture lebih berguna sebagai kerangka konseptual daripada model kernel yang berdiri sendiri.

## Kesimpulan
Model yang paling relevan untuk sistem operasi modern adalah hybrid kernel, yaitu kombinasi antara monolithic dan microkernel. Contoh nyata adalah Windows NT (Windows modern) dan macOS/iOS. Hybrid kernel berusaha mengambil performa monolithic sekaligus modularitas dan keandalan microkernel. Untuk sistem server dan cloud, Linux (monolithic dengan modul dinamis) mendominasi. Untuk perangkat mobile dan embedded, microkernel atau hybrid kernel lebih dipilih.

Dengan demikian, tidak ada satu model yang mutlak terbaik; yang relevan adalah penerapan kernel hybrid dan modular yang menyesuaikan kebutuhan spesifik: performa untuk server, keandalan untuk embedded, dan fleksibilitas untuk desktop.

## Quiz
1. Sebutkan tiga fungsi utama sistem operasi: Manajemen Sumber Daya,Manajemen File,dan Sistem Antarmuka Pengguna
2. Jelaskan perbedaan antara keKernel Mode: Akses penuh ke seluruh sistem. Digunakan oleh sistem operasi. Kesalahan bisa menyebabkan sistem crash.
User Mode: Akses terbatas. Digunakan oleh aplikasi pengguna. Kesalahan hanya memengaruhi program, bukan seluruh sistem.rnel mode dan user mode.
3. Sebutkan contoh OS dengan arsitektur monolithic dan microkernel.
Monolithic Kernel: Linux MS-DOS UNIX
Microkernel: Minix QNX MacOS

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?
- Hal yang saya rasakan dan paling menantang pada minggu ini yaitu pada bagian dimana saya belajar proses instalasi dan konfigurasi WSL, karena saya harus memahami hubungan antara Windows dan Linux sebelum saya menjalankan programnya, karena sebelumnya saya belum pernah mencoba menggunakan Ubuuntu, saya merasa tertantang tetapi sedikit takut dan was was karena saya mencobanya menggunakan laptop pribadi, sebelum itu saya mencoba untuk memahami konsep kernel dan system call sebelum saya memulai praktikum, meskipun hasil percobaan berjalan dengan baik tetap ada rasa ragu dan bingung. 
- Bagaimana cara Anda mengatasinya?
- Untuk mengatasi tantangan tersebut, saya mencari referensi dari internet seperti google, youtube dan beberapa panduan online, untuk melihat tutorial instalasi dengan benar sehingga tidak terjadi crash dan kesalahan yang lain. Dan tetap berusaha meyakinkan diri saya bahwa saya bis

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
