# SR-03: Event Loop Phases - The Lifecycle of a Request

Membahas detail siklus hidup pemrosesan asinkron di dalam Node.js, fase demi fase.

## 🎯 The Why (Visi Arsitektural)
Berbeda dengan browser, Event Loop di Node.js memiliki tahapan yang sangat spesifik untuk operasi server. Mengetahui urutan fase ini krusial untuk memprediksi perilaku aplikasi saat menangani ribuan permintaan bersamaan dan menghindari bug "racing condition".

## 🏗️ The How (Arsitektur Internal)
Satu putaran (tick) Event Loop terdiri dari fase berikut:
1.  **Timers**: Mengeksekusi callback `setTimeout` dan `setInterval`.
2.  **Pending Callbacks**: Menangani sisa callback I/O untuk sistem tertentu.
3.  **Poll**: Mengambil event I/O baru (koneksi masuk, data file).
4.  **Check**: Tempat khusus bagi `setImmediate`.
5.  **Close Callbacks**: Membersihkan sumber daya (misal `socket.on('close', ...)`).
*Catatan: Microtasks (`nextTick`, `Promise`) disisipkan di antara setiap fase.*

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Phase Sequencing Logic**: Eksperimen urutan eksekusi antara Timer, Immediate, dan I/O.
- **BK-02: NextTick vs Promises**: Urutan prioritas di dalam antrean microtask.
- **BK-03: Event Loop Monitoring**: Mendeteksi kelambatan loop menggunakan `perf_hooks`.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Process.nextTick Abuse**: Rekursi di `nextTick` akan memblokir masuknya loop ke fase berikutnya, menyebabkan "I/O Starvation".
- **Poll Phase Spin**: Jika banyak I/O masuk, loop bisa terjebak di fase Poll terlalu lama, menunda eksekusi fase Timers.
- **Unpredictable setImmediate**: Di luar callback I/O, urutan antara `setTimeout(0)` dan `setImmediate` tidak deterministik.

---
## 📖 Daftar Buku (Books)
*Belum diinisialisasi.*
