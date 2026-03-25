# SR-01: JS Node Orchestration - The Core Alliance

Membahas hubungan intim antara standar JavaScript (V8) dan API native Node.js untuk orkestrasi aplikasi server.

## 🎯 The Why (Visi Arsitektural)
Node.js bukan hanya JS yang dipindahkan ke server; ia adalah aliansi antara eksekusi logika (V8) dan otoritas sistem (Libuv). Memahami orkestrasi ini krusial untuk membangun layanan backend yang tidak hanya berfungsi secara logika, tapi juga memanfaatkan setiap tetes tenaga mesin server.

## 🏗️ The How (Arsitektur Internal)
Orkestrasi ini melibatkan:
1.  **Global Objects Implementation**: Bagaimana `process`, `Buffer`, dan `require` disuntikkan ke dalam scope JavaScript.
2.  **Asynchronous Bridge**: Bagaimana V8 memarkir eksekusi JS sementara menunggu sinyal penyelesaian I/O dari Libuv.
3.  **Bootstrap Process**: Alur inisialisasi runtime dari saat perintah `node` dijalankan hingga skrip pengguna dieksekusi.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Runtime Bootstrapping**: Menelusuri apa yang terjadi di milidetik pertama startup Node.js.
- **BK-02: Global Scoping & Environment**: Mengelola variabel lingkungan dan parameter global secara efisien.
- **BK-03: Event Emitter Architecture**: Fondasi komunikasi antar modul di dalam engine.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Global Pollution**: Menabrakkan variabel global dapat merusak optimalisasi V8 dan membingungkan dependensi pihak ketiga.
- **Blocking the Event Loop**: Kesalahpahaman bahwa JavaScript di server bisa melakukan kalkulasi berat tanpa mengunci antrean I/O pengguna lain.
- **Memory Overhead of Globals**: Terlalu banyak data yang disimpan di scope global tidak akan pernah bisa dibersihkan oleh Garbage Collector.
