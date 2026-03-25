# SR-02: V8 Bindings - The System Bridge

Membahas bagaimana Node.js menjembatani dunia JavaScript (V8) dengan dunia Sistem Operasi (C++).

## 🎯 The Why (Visi Arsitektural)
JavaScript secara native tidak memiliki akses ke sistem berkas atau jaringan. V8 Bindings adalah "penerjemah" yang memungkinkan kode JS memanggil fungsi native C++ yang memiliki otoritas penuh atas perangkat keras, memberikan kekuatan sistem kepada bahasa web.

## 🏗️ The How (Arsitektur Internal)
Mekanisme penjembatanan ini berevolusi melalui beberapa lapisan:
1.  **V8 C++ API**: Antarmuka langsung V8. Sangat cepat tapi sulit dipertahankan karena sering berubah antar versi.
2.  **NAN (Native Abstractions for Node.js)**: Lapisan makro untuk mendukung berbagai versi Node.js.
3.  **N-API / Node-API**: API C stabil yang menjamin kompatibilitas biner lintas versi Node.js (ABI Stable).

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Node-API Deep Dive**: Membangun modul native pertama untuk performa ekstrem.
- **BK-02: Wrapping C++ Classes**: Mengekspos objek C++ ke dalam ruang lingkup JavaScript.
- **BK-03: Performance Overhead Analysis**: Mengukur biaya "crossing the bridge" antara JS dan C++.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Context Switching Cost**: Terlalu sering memanggil fungsi native yang kecil dapat mengakibatkan overhead komunikasi yang melebihi keuntungan performa native.
- **Memory Management Mismatch**: Kebocoran memori sering terjadi saat objek dialokasikan di sisi C++ tapi tidak dibersihkan dengan benar saat objek JS-nya terkena Garbage Collection.
- **Threading Dangers**: Memanggil API V8 dari thread luar tanpa pengamanan yang tepat dapat mengakibatkan *crash* seketika.
