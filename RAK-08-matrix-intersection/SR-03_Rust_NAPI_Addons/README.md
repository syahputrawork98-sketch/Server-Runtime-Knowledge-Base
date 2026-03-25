# SR-03: Rust NAPI Addons - The Performance Beast

Membahas penggunaan Rust untuk menulis modul Node.js dengan performa ekstrem dan keamanan memori yang jauh lebih baik dibanding C++.

## 🎯 The Why (Visi Arsitektural)
Saat Node.js mencapai batas performanya, Rust adalah pilihan terbaik untuk ekspansi. Melalui N-API, kita bisa mengintegrasikan Rust ke dalam ekosistem Node.js, mendapatkan kecepatan bahasa sistem tanpa risiko kebocoran memori (Memory Safety) yang sering menghantui C++.

## 🏗️ The How (Arsitektur Internal)
Integrasi diperkuat oleh:
1.  **Napi-rs**: Kerangka kerja modern yang memudahkan penulisan Node Addons menggunakan idiomatik Rust.
2.  **ABI Stability**: Menjamin modul Rust tetap berfungsi meskipun versi Node.js diperbarui.
3.  **Efficient Data Transfer**: Strategi memindahkan data besar dari JavaScript ke Rust tanpa penyalinan memori yang mahal.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Rust-Node Project Setup**: Menyiapkan workflow `napi-rs` di dalam monorepo.
- **BK-02: Advanced Async Addons**: Menjalankan tugas berat di thread Rust dan mengembalikan hasilnya ke JS via Promise.
- **BK-03: Zero-copy Buffer Interaction**: Manipulasi data biner langsung di memori bersama.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Compilation Time**: Kompilasi Rust jauh lebih lambat dibanding JavaScript murni; ini memerlukan strategi caching yang baik di CI/CD.
- **Complex Interop Types**: Mengirimkan struktur data yang sangat kompleks antar bahasa memerlukan desain API yang hati-hati untuk menghindari kebingungan.
- **Cargo-NPM Discrepancy**: Mengelola dua manajer paket (Cargo untuk Rust dan NPM untuk JS) dalam satu proyek menambah lapisan manajemen dependensi.
