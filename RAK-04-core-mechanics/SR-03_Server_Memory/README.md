# SR-03: Server Memory - Scaling Higher

Membahas manajemen memori tingkat lanjut pada sisi server untuk mendukung aplikasi berskala enterprise.

## 🎯 The Why (Visi Arsitektural)
Server seringkali menangani data yang jauh lebih besar daripada browser. Tanpa optimasi memori yang tepat, server akan sering terkena "Garbage Collection Storms" yang memperlambat respon aplikasi atau mati karena kehabisan RAM.

## 🏗️ The How (Arsitektur Internal)
Manajemen memori server melibatkan:
1.  **V8 Heap Limits**: Mengatur batas memori eksplisit (`--max-old-space-size`) agar sesuai dengan kapasitas server (misal di Docker).
2.  **External Memory (Buffers)**: Mengalokasikan data di luar Heap V8 untuk menghindari beban pada Garbage Collector saat menangani data biner besar.
3.  **Memory Profiling**: Melacak tumpukan objek dan pencarian kebocoran memori pada aplikasi yang berjalan lama (long-running).

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Heap Tuning & Monitoring**: Strategi pengaturan memori untuk berbagai lingkungan (Small VM vs High-mem Server).
- **BK-02: Core Dumps & Snapshots**: Menganalisis kondisi memori saat server mengalami crash.
- **BK-03: Garbage Collection Optimization**: Mengurangi durasi "Stop-The-World" pada aplikasi real-time.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Buffer Bloat**: Mengalokasikan Buffer secara berlebihan di luar Heap dapat menyebabkan OS melakukan pembunuhan proses (OOM Killer) secara tiba-tiba.
- **Hidden Leaks in Modules**: Dependensi pihak ketiga yang tidak dikelola dengan baik seringkali menjadi sumber kebocoran memori utama di server.
- **Large Heap Latency**: Heap yang sangat besar (misal 16GB+) akan mengakibatkan jeda Garbage Collection yang sangat lama jika tidak dioptimalkan.
