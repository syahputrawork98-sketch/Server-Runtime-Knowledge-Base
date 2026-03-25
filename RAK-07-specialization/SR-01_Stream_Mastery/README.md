# SR-01: Stream Mastery - High-Performance Data Flow

Membahas paradigma pemrosesan data aliran (Streams) di Node.js untuk efisiensi memori yang ekstrem.

## 🎯 The Why (Visi Arsitektural)
Menangani data besar (misal: file 10GB atau streaming video live) tidak mungkin dilakukan dengan memuat seluruh data ke dalam RAM. Streams memungkinkan kita memproses data sepotong demi sepotong (*piece-by-piece*), menjaga konsumsi memori sekecil mungkin bahkan saat menangani beban kerja raksasa.

## 🏗️ The How (Arsitektur Internal)
Terdapat empat jenis fundamental aliran data:
1.  **Readable**: Sumber data (misal: File atau Response HTTP).
2.  **Writable**: Tujuan data (misal: Penulisan file atau Request HTTP).
3.  **Duplex**: Aliran dua arah (misal: Sockets).
4.  **Transform**: Memodifikasi data saat mengalir (misal: Kompresi Gzip atau Enkripsi).
5.  **Backpressure**: Mekanisme koordinasi saat penulis data lebih lambat dari pembaca data.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Built-in Streams Patterns**: Menguasai penggunaan `.pipe()` dan `pipeline()` untuk aliran data aman.
- **BK-02: Custom Transform Streams**: Membangun logika pemrosesan data (seperti parser CSV) berbasis stream.
- **BK-03: Handling Backpressure**: Strategi mencegah kebocoran memori saat aliran data tersumbat.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Memory Leaks on Error**: Jika terjadi error pada aliran yang tidak menggunakan `pipeline()`, sumber daya (seperti file handle) seringkali tidak tertutup otomatis.
- **Event-Stream Trap**: Mencampur paradigma Event (`on('data')`) dengan Stream API modern dapat menyebabkan perilaku yang tidak konsisten.
- **Performance Overhead**: Menggunakan terlalu banyak Transform stream berlebihan untuk tugas kecil dapat menambahkan latensi CPU yang tidak perlu.
