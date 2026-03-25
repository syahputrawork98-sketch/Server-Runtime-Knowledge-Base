# SR-02: Parallelism Patterns - Scaling Across Cores

Membahas strategi untuk mendistribusikan beban kerja ke seluruh core CPU yang tersedia guna mencapai throughput sistem yang maksimal.

## 🎯 The Why (Visi Arsitektural)
Satu instance Node.js hanya berjalan pada satu core CPU. Pada server modern dengan puluhan core, membiarkan core lain menganggur adalah pemborosan. Paralelisme memungkinkan aplikasi untuk menangani ribuan permintaan tambahan tanpa penambahan biaya perangkat keras yang signifikan.

## 🏗️ The How (Arsitektur Internal)
Paralelisme di Node.js dapat dicapai melalui beberapa pola:
1.  **Cluster Module**: Menkloning proses utama menjadi beberapa proses anak (fork) yang berbagi port jaringan yang sama (Round-robin).
2.  **Child Processes**: Menjalankan perintah eksternal atau skrip JS lain di proses yang benar-benar terpisah dengan memori mandiri.
3.  **IPC (Inter-Process Communication)**: Jalur komunikasi khusus untuk mengirim objek JSON antar proses yang berbeda.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Clustering for High Availability**: Membangun klaster server yang tahan banting (Auto-restart on crash).
- **BK-02: Child Process Mastery**: Menggunakan `spawn`, `exec`, dan `fork` untuk koordinasi tugas lintas proses.
- **BK-03: Advanced IPC Communication**: Strategi sinkronisasi status antar proses klaster tanpa database eksternal.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Shared State Paradox**: Karena proses klaster tidak berbagi memori, status aplikasi (seperti sesi login) harus disimpan di luar (misal: Redis).
- **IPC Overhead**: Mengirim terlalu banyak data melalui IPC dapat membebani CPU karena proses serialisasi/deserialisasi JSON yang intensif.
- **Load Balancing Unfairness**: Cluster standar kadang tidak membagi beban secara merata pada jenis beban I/O tertentu; terkadang diperlukan penyeimbang beban (Load Balancer) eksternal (NGINX/HAProxy).
