# SR-02: Threading Internals - Beyond Single-Threaded

Membahas bagaimana Node.js mengelola multi-threading secara internal dan bagaimana pengembang dapat memanfaatkan paralelisme secara eksplisit.

## 🎯 The Why (Visi Arsitektural)
Meskipun Node.js terkenal dengan "Single-Threaded" Event Loop-nya, duni server menuntut paralelisme untuk tugas-tugas intensif CPU. Tanpa pemahaman mendalam tentang threading, satu tugas berat dapat melumpuhkan seluruh server dan menolak ribuan permintaan masuk.

## 🏗️ The How (Arsitektur Internal)
Eksekusi paralel dikelola melalui dua jalur:
1.  **Internal Thread Pool (Libuv)**: Digunakan secara otomatis untuk I/O asinkron tertentu (FS, Crypto).
2.  **Worker Threads**: Memungkinkan pengembang membuat thread eksekusi JavaScript baru yang berjalan paralel dengan Main Thread.
3.  **SharedArrayBuffer & Atomics**: Komunikasi rendah tingkat antar thread untuk berbagi memori tanpa overhead salinan data.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Worker Threads Mastery**: Strategi memindahkan kalkulasi berat ke thread terpisah.
- **BK-02: Shared Memory Patterns**: Optimasi komunikasi antar thread untuk dataset besar.
- **BK-03: Thread Pool Tuning**: Mengoptimalkan `UV_THREADPOOL_SIZE` untuk throughput server maksimum.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Worker Overhead**: Menjalankan thread baru memakan memori (Isolate V8 baru). Terlalu banyak thread akan membuat server kehabisan RAM.
- **Context Switching Cost**: Terlalu sering berpindah antar thread dapat menghabiskan waktu CPU lebih banyak daripada melakukan tugasnya itu sendiri.
- **Race Conditions**: Kesalahan penggunaan `SharedArrayBuffer` tanpa `Atomics` dapat mengakibatkan data yang rusak dan bug yang sulit dilacak.
