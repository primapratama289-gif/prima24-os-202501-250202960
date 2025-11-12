
# Laporan Praktikum Minggu [5]
Topik: Penjadwalan CPU – FCFS dan SJF

---

## Identitas
- **Nama**  : Prima Radita Pratama
- **NIM**   : 250202960
- **Kelas** : 1IKRA

---

## Tujuan
Setelah menyelesaikan tugas ini, mahasiswa mampu:

1. Menghitung waiting time dan turnaround time untuk algoritma FCFS dan SJF.
2. Menyajikan hasil perhitungan dalam tabel yang rapi dan mudah dibaca.
3. Membandingkan performa FCFS dan SJF berdasarkan hasil analisis.
4. Menjelaskan kelebihan dan kekurangan masing-masing algoritma.
5. Menyimpulkan kapan algoritma FCFS atau SJF lebih sesuai digunakan.
---

## Dasar Teori
Pada praktikum minggu ini, mahasiswa akan mempelajari **algoritma penjadwalan CPU (CPU Scheduling)** menggunakan dua pendekatan dasar:  
- **FCFS (First Come First Served)**  
- **SJF (Shortest Job First)**  

Tujuan utamanya adalah memahami bagaimana sistem operasi menentukan urutan eksekusi proses, serta bagaimana *waiting time* dan *turnaround time* memengaruhi performa sistem.

Mahasiswa akan melakukan simulasi dan perbandingan hasil perhitungan kedua algoritma ini menggunakan **tabel observasi manual atau spreadsheet (Excel/Google Sheets)** — tanpa perlu melakukan instalasi atau pemrograman tambahan.

---

## Langkah Praktikum
1. **Siapkan Data Proses**
   Gunakan tabel proses berikut sebagai contoh (boleh dimodifikasi dengan data baru):
   | Proses | Burst Time | Arrival Time |
   |:--:|:--:|:--:|
   | P1 | 6 | 0 |
   | P2 | 8 | 1 |
   | P3 | 7 | 2 |
   | P4 | 3 | 3 |

2. **Eksperimen 1 – FCFS (First Come First Served)**
   - Urutkan proses berdasarkan *Arrival Time*.  
   - Hitung nilai berikut untuk tiap proses:
     ```
     Waiting Time (WT) = waktu mulai eksekusi - Arrival Time
     Turnaround Time (TAT) = WT + Burst Time
     ```
   - Hitung rata-rata Waiting Time dan Turnaround Time.  
   - Buat Gantt Chart sederhana:  
     ```
     | P1 | P2 | P3 | P4 |
     0    6    14   21   24
     ```

3. **Eksperimen 2 – SJF (Shortest Job First)**
   - Urutkan proses berdasarkan *Burst Time* terpendek (dengan memperhatikan waktu kedatangan).  
   - Lakukan perhitungan WT dan TAT seperti langkah sebelumnya.  
   - Bandingkan hasil FCFS dan SJF pada tabel berikut:

     | Algoritma | Avg Waiting Time | Avg Turnaround Time | Kelebihan | Kekurangan |
     |------------|------------------|----------------------|------------|-------------|
     | FCFS | ... | ... | Sederhana dan mudah diterapkan | Tidak efisien untuk proses panjang |
     | SJF | ... | ... | Optimal untuk job pendek | Menyebabkan *starvation* pada job panjang |

4. **Eksperimen 3 – Visualisasi Spreadsheet (Opsional)**
   - Gunakan Excel/Google Sheets untuk membuat perhitungan otomatis:
     - Kolom: Arrival, Burst, Start, Waiting, Turnaround, Finish.
     - Gunakan formula dasar penjumlahan/subtraksi.
   - Screenshot hasil perhitungan dan simpan di:
     ```
     praktikum/week5-scheduling-fcfs-sjf/screenshots/
     ```

5. **Analisis**
   - Bandingkan hasil rata-rata WT dan TAT antara FCFS & SJF.  
   - Jelaskan kondisi kapan SJF lebih unggul dari FCFS dan sebaliknya.  
   - Tambahkan kesimpulan singkat di akhir laporan.

6. **Commit & Push**
   ```bash
   git add .
   git commit -m "Minggu 5 - CPU Scheduling FCFS & SJF"
   git push origin main
   ```
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
<img width="720" height="567" alt="Week5 png" src="https://github.com/user-attachments/assets/d96bc62d-1ce7-4f08-9064-cedf512584f9" />

---

## Eksperimen 3 Perbandingan FCFS & SJF
| Algoritma | Avg Waiting Time | Avg Turnaround Time | Kelebihan | Kekurangan |
|------------|------------------|----------------------|------------|-------------|
| FCFS | 8,75 | 14,75 | Sederhana dan mudah diterapkan | Tidak efisien untuk proses panjang |
| SJF | 6,25 | 12,25 | Optimal untuk job pendek | Menyebabkan starvation pada job panjang |

---

## Analisis
Analisis Algoritma FCFS (First Come First Served)
Berdasarkan hasil perhitungan, algoritma FCFS menghasilkan Average Waiting Time (AWT) sebesar 8,75 dan Average Turnaround Time (ATT) sebesar 14,75. Nilai ini menunjukkan bahwa proses yang datang lebih awal akan langsung dieksekusi terlebih dahulu tanpa memperhatikan waktu eksekusi (Burst Time). Namun, hal ini menimbulkan efek convoy effect, di mana proses yang memiliki Burst Time pendek harus menunggu proses yang lebih lama selesai terlebih dahulu. Akibatnya, efisiensi CPU berkurang karena total waktu tunggu menjadi cukup besar.

Analisis Algoritma SJF (Shortest Job First)
Pada algoritma SJF, hasil perhitungan menunjukkan Average Waiting Time (AWT) sebesar 6,25 dan Average Turnaround Time (ATT) sebesar 12,25. Nilai ini lebih rendah dibandingkan dengan FCFS, yang berarti algoritma SJF lebih efisien dalam mengurangi waktu tunggu dan penyelesaian proses. Hal ini terjadi karena SJF memprioritaskan proses dengan waktu eksekusi (Burst Time) terpendek, sehingga dapat meningkatkan throughput dan mengurangi penundaan.

Perbandingan dan Kesimpulan Analisis
Dari hasil kedua eksperimen, terlihat bahwa algoritma SJF memberikan performa yang lebih optimal dibandingkan FCFS, karena mampu menurunkan rata-rata waktu tunggu dan waktu penyelesaian. Akan tetapi, penerapan SJF memerlukan estimasi waktu eksekusi setiap proses secara akurat, dan dalam sistem nyata hal ini tidak selalu mudah dilakukan.
Sementara itu, FCFS tetap unggul dalam kesederhanaan dan keadilan (fairness), karena setiap proses dilayani sesuai urutan kedatangan tanpa diskriminasi waktu eksekusi.

---

## Kesimpulan
1. Algoritma FCFS (First Come First Served) memberikan hasil yang lebih sederhana dan mudah diimplementasikan, namun memiliki kelemahan yaitu waiting time dan turnaround time rata-rata lebih tinggi karena proses dengan waktu eksekusi pendek bisa tertunda oleh proses yang lebih lama.

2. Algoritma SJF (Shortest Job First) menghasilkan performa yang lebih baik dibandingkan FCFS dengan average waiting time dan average turnaround time yang lebih rendah, karena proses dengan waktu eksekusi lebih singkat dieksekusi lebih dahulu.

3. Dari hasil perbandingan, dapat disimpulkan bahwa SJF lebih efisien dalam meminimalkan waktu tunggu dan waktu penyelesaian, namun penerapannya lebih kompleks karena memerlukan estimasi waktu eksekusi (burst time) yang akurat.

---

## Quiz
1. Apa perbedaan utama antara FCFS dan SJF?

jawaban:Perbedaan utama antara FCFS (First Come First Served) dan SJF (Shortest Job First) terletak pada cara menentukan urutan proses yang dieksekusi. FCFS menjalankan proses berdasarkan urutan kedatangan, sehingga proses yang datang lebih dulu akan dikerjakan lebih dulu tanpa memperhatikan lama eksekusi. Sementara itu, SJF memilih proses dengan waktu eksekusi paling pendek untuk dijalankan terlebih dahulu agar waktu tunggu rata-rata lebih efisien. FCFS mudah diterapkan tetapi kurang efisien, sedangkan SJF lebih cepat namun memerlukan perkiraan waktu eksekusi tiap proses.

2. Mengapa SJF dapat menghasilkan rata-rata waktu tunggu minimum?

jawaban:SJF atau Shortest Job First dapat menghasilkan rata-rata waktu tunggu minimum karena algoritma ini selalu mengeksekusi proses dengan waktu eksekusi paling pendek terlebih dahulu. Dengan cara tersebut, proses yang membutuhkan waktu singkat dapat segera selesai tanpa harus menunggu proses yang lebih lama. Akibatnya, total waktu tunggu semua proses menjadi lebih kecil dibandingkan jika proses dengan waktu panjang dijalankan lebih awal. Karena itulah, SJF dianggap sebagai algoritma yang paling efisien dalam meminimalkan waktu tunggu rata-rata, meskipun memerlukan perkiraan waktu eksekusi yang tidak selalu mudah diketahui.

3. Apa kelemahan SJF jika diterapkan pada sistem interaktif?

jawaban:Kelemahan SJF jika diterapkan pada sistem interaktif adalah algoritma ini tidak cocok untuk menangani proses yang membutuhkan respons cepat. Dalam sistem interaktif, pengguna biasanya mengharapkan proses dijalankan segera setelah memberikan input. Namun, SJF dapat menyebabkan proses dengan waktu eksekusi panjang terus-menerus tertunda karena proses yang lebih pendek selalu diprioritaskan. Akibatnya, proses besar bisa mengalami penundaan yang lama atau bahkan tidak pernah mendapat giliran eksekusi, yang disebut dengan istilah starvation. Selain itu, sulit untuk memperkirakan waktu eksekusi proses secara akurat pada sistem interaktif, sehingga penerapan SJF menjadi kurang efektif dan tidak praktis.
---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
