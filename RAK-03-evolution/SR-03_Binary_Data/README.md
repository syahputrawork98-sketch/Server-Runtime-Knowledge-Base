# SR-03: Binary Data - Beyond Text

Membahas bagaimana Server Runtime mengelola data biner mentah yang krusial untuk performa tinggi dan interoperabilitas sistem.

## 🎯 The Why (Visi Arsitektural)
JavaScript awalnya dirancang untuk teks (string). Namun, server harus menangani gambar, video, dan protokol biner. Tanpa manipulasi biner yang efisien, server akan membuang banyak waktu hanya untuk konversi data yang tidak perlu.

## 🏗️ The How (Arsitektur Internal)
Manajemen data biner di Node.js mengandalkan:
1.  **Buffer**: Kelas khusus untuk mengalokasikan memori di luar V8 heap (fixed size).
2.  **TypedArrays**: Standar JavaScript modern untuk mengakses data biner mentah.
3.  **Encodings**: Transformasi antara biner dan teks (UTF-8, Base64, Hex).

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Buffer Manipulation & Safety**: Mengelola memori biner dengan aman tanpa risiko `out-of-bounds`.
- **BK-02: Binary Protocols Parsing**: Implementasi parser biner kustom (misal: MQTT, custom IPC).
- **BK-03: Streams & Binary Interop**: Hubungan antara aliran data dan alokasi buffer.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Buffer Recycling Risk**: Menggunakan `Buffer.allocUnsafe` tanpa membersihkan data lama dapat membocorkan informasi sensitif dari memori.
- **Memory Fragmentation**: Alokasi buffer besar secara terus-menerus dapat menyebabkan fragmentasi memori di level OS.
- **Conversion Overhead**: Terlalu sering mengubah antara Buffer dan String dapat membebani CPU secara signifikan.
