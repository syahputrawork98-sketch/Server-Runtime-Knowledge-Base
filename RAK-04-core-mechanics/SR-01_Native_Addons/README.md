# SR-01: Native Addons - Extending the Runtime

Membahas bagaimana memperluas kemampuan Node.js melintasi batas JavaScript dengan menulis modul native dalam C++, Rust, atau C.

## 🎯 The Why (Visi Arsitektural)
Terkadang JavaScript tidak cukup cepat untuk komputasi berat (seperti kompresi video atau enkripsi tingkat tinggi) atau tidak memiliki akses langsung ke pustaka sistem tertentu. Native Addons memungkinkan kita memanfaatkan performa mentah perangkat keras sambil tetap menggunakan kemudahan JavaScript di lapisan atas.

## 🏗️ The How (Arsitektur Internal)
Modul native di Node.js berevolusi menjadi standar modern:
1.  **Node-API (N-API)**: API C yang stabil secara ABI (Application Binary Interface), memastikan modul yang dikompilasi untuk satu versi Node.js tetap berfungsi di versi masa depan tanpa kompilasi ulang.
2.  **Headers & Tooling**: Penggunaan `node-gyp` atau `cmake-js` untuk proses build.
3.  **Wrappers**: Menggunakan `node-addon-api` untuk abstraksi C++ yang lebih bersih.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Node-API Essentials**: Membangun modul "Hello World" native pertama.
- **BK-02: Data Marshalling & Conversion**: Memindahkan data besar antara Buffer JS dan array C++ secara efisien.
- **BK-03: Rust with N-API**: Menggunakan keamanan Rust untuk menulis Node Addons (melalui `napi-rs`).

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Build Complexity**: Mengelola dependensi native di berbagai platform (Windows/Linux/macOS) adalah tantangan besar dalam CI/CD.
- **Memory Corruption**: Kesalahan manajemen memori di kode native (C++) tidak akan tertangkap oleh JS dan dapat menyebabkan *Segmentation Fault* yang menghentikan seluruh server.
- **Upgrade Fragility**: Modul lama yang tidak menggunakan N-API akan pecah setiap kali ada pembaruan versi mayor Node.js.
