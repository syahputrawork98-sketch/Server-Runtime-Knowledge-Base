# SR-01: Libuv Core - The Engine of Asynchrony

Membahas arsitektur `libuv`, perpustakaan C yang memberikan kemampuan I/O asinkron multi-platform kepada Node.js.

## 🎯 The Why (Visi Arsitektural)
Node.js dirancang untuk skalabilitas I/O yang masif tanpa menggunakan banyak thread. `libuv` adalah "jantung" yang memungkinkan ribuan koneksi jaringan ditangani secara konkuren pada satu thread utama, menghindari overhead memori yang besar.

## 🏗️ The How (Arsitektur Internal)
`libuv` menggunakan dua mekanisme utama:
1.  **Event Loop**: Menggunakan abstraksi OS tingkat rendah seperti `epoll` (Linux), `kqueue` (macOS), dan `IOCP` (Windows) untuk menangani I/O jaringan tanpa hambatan.
2.  **Thread Pool**: Digunakan untuk tugas yang tidak memiliki API asinkron dari OS (seperti operasi File System atau Kriptografi), secara default menyediakan 4 thread pembantu.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: I/O Polling Mechanics**: Memahami bagaimana `epoll` dan kawan-kawan bekerja di balik layar.
- **BK-02: Thread Pool Orchestration**: Mengelola `UV_THREADPOOL_SIZE` dan dampaknya pada performa Disk/Crypto.
- **BK-03: Platform Abstractions**: Bagaimana `libuv` menyatukan perbedaan kernel antar OS.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Thread Pool Exhaustion**: Operasi File System yang terlalu banyak dapat memenuhi thread pool dan membuat operasi lain (seperti DNS lookup) tertunda.
- **Single Threaded CPU Bound**: `libuv` tidak membantu jika kode JS Anda melakukan kalkulasi matematika berat (ini akan memblokir seluruh loop).
- **Callback Hell & Starvation**: Pola asinkron yang salah dapat mengakibatkan degradasi performa yang sulit dilacak.
