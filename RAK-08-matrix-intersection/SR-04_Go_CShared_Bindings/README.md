# SR-04: Go CShared Bindings - System Interop

Membahas penggunaan bahasa Go sebagai perpustakaan sistem yang dapat dipanggil oleh Node.js untuk tugas-tugas paralelisme tinggi.

## 🎯 The Why (Visi Arsitektural)
Go memiliki manajemen konkurensi (Goroutines) yang luar biasa. Dengan mengubah kode Go menjadi perpustakaan bersama (`.so` atau `.dll`), kita dapat memberikan kemampuan paralelisme masif Go ke dalam satu proses Node.js, sangat cocok untuk integrasi sistem warisan atau algoritma khusus.

## 🏗️ The How (Arsitektur Internal)
Komunikasi dilakukan melalui:
1.  **CGO & C-Shared Build**: Mengompilasi paket Go menjadi format pustaka yang dimengerti oleh sistem operasi (C-compatible).
2.  **FFI (Foreign Function Interface)**: Penggunaan modul JS (seperti `koffi` atau `node-ffi-napi`) untuk memanggil fungsi dari pustaka biner tersebut.
3.  **Data Serialization**: Konversi tipe data Go (seperti string atau struct) menjadi representasi biner yang dapat diproses oleh C/JS.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Building C-Shared Libraries**: Langkah demi langkah kompilasi Go untuk Node.js.
- **BK-02: Calling Go from JS via FFI**: Implementasi jembatan pemanggilan fungsi lintas bahasa.
- **BK-03: Concurrent Workflows with Go**: Menjalankan goroutine di balik API Node.js.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **The FFI Performance Tax**: Memanggil fungsi melalui FFI memiliki overhead latensi yang lebih besar dibanding native bindings (N-API). Tidak disarankan untuk pemanggilan fungsi mikro ribuan kali per detik.
- **Garbage Collector Conflict**: Go dan V8 memiliki GC-nya masing-masing. Salah mengelola pointer antar keduanya dapat mengakibatkan crash memori yang "senyap".
- **Debugging Blind Spot**: Alat debug JS tidak bisa melihat ke dalam kode Go yang sudah dikompilasi, memerlukan debugger level sistem (GDB/LLDB).
