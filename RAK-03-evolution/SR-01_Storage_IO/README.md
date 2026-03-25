# SR-01: Storage I/O - The Physical Interface

Membahas bagaimana Server Runtime (Node.js) berinteraksi dengan sistem penyimpanan fisik (Disk) melalui abstraksi file system.

## 🎯 The Why (Visi Arsitektural)
Pada sisi server, kecepatan I/O (Input/Output) sering kali menjadi hambatan utama performa. Memahami bagaimana runtime mengelola pembacaan dan penulisan berkas secara non-blocking sangat krusial untuk aplikasi intensif data seperti database atau pemrosesan media.

## 🏗️ The How (Arsitektur Internal)
Node.js menggunakan modul `fs` yang ditenagai oleh `libuv` thread pool:
1.  **Synchronous APIs**: Memblokir eksekusi hingga operasi selesai (hanya untuk skrip inisialisasi).
2.  **Asynchronous Callbacks/Promises**: Melempar tugas ke `libuv` dan melanjutkan eksekusi.
3.  **Streams**: Memproses data dalam potongan kecil (*chunks*) untuk efisiensi memori tingkat tinggi.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: File System Abstractions**: Membedah detail modul `fs` dan `path`.
- **BK-02: Stream Processing Patterns**: Menggunakan `Pipe` untuk memindahkan data tanpa membebani RAM.
- **BK-03: Buffer & Binary I/O**: Mengelola data biner mentah secara efisien di level memori.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Thread Pool Starvation**: Terlalu banyak operasi I/O simultan yang berat dapat menghabiskan thread pool bawaan (default 4).
- **Resource Leaks**: Lupa menutup *file descriptors* dapat menyebabkan sistem kehabisan batas akses berkas (EMFILE).
- **Synchronous Trap**: Menggunakan fungsi `Sync` di dalam jalur permintaan (request path) akan menghancurkan skalabilitas server.
