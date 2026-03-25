# SR-01: Module System - The Architecture of Logic

Membahas bagaimana Node.js mengelola pemecahan kode menjadi bagian-bagian kecil (modul) dan pertempuran evolusi antara CommonJS dan ECMAScript Modules (ESM).

## 🎯 The Why (Visi Arsitektural)
Aplikasi server skala besar tidak mungkin ditulis dalam satu berkas raksasa. Sistem modul memberikan keteraturan, enkapsulasi, dan kemudahan dalam pengujian (testing). Tanpa pemahaman mendalam tentang modul, dependensi aplikasi akan menjadi "spaghetti code" yang mustahil dikelola.

## 🏗️ The How (Arsitektur Internal)
Node.js mendukung dua sistem modularitas:
1.  **CommonJS (CJS)**: Sistem modul lawas berbasis `require()`, bersifat sinkron, dan memuat modul saat runtime.
2.  **ES Modules (ESM)**: Standar resmi JavaScript berbasis `import/export`, bersifat asinkron, dan memungkinkan optimasi seperti `Tree Shaking` di sisi kompilasi.
3.  **Module Resolution Algorithm**: Bagaimana Node.js mencari lokasi berkas fisik berdasarkan nama string (Lookup logic di `node_modules`).

## 🧪 The Practical (Roadmap Buku)
- **BK-01: CommonJS vs ESM Interop**: Strategi menggabungkan dua dunia sistem modul dalam satu proyek.
- **BK-02: Package Exports & Scopes**: Menguasai properti `exports` di `package.json` untuk pengemasan modern.
- **BK-03: Dependency Resolution & Lockfiles**: Mengelola pohon dependensi dan menjaga konsistensi tim.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Circular Dependencies**: Situasi di mana dua modul saling memanggil satu sama lain, sering menyebabkan error `undefined` pada ekspor.
- **ESM-only Package Trap**: Menggunakan paket yang hanya mendukung ESM di proyek CJS lama memerlukan konfigurasi transpilasi yang rumit.
- **Cache Side-effects**: Modul di Node.js di-cache setelah pemuatan pertama; mutasi pada objek modul yang diekspor dapat berdampak pada seluruh aplikasi.
