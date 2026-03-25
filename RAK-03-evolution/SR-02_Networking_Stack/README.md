# SR-02: Networking Stack - The Server's Voice

Membahas lapisan jaringan dari level rendah hingga protokol aplikasi yang memungkinkan server berkomunikasi dengan klien dan layanan lain.

## 🎯 The Why (Visi Arsitektural)
Server pada dasarnya adalah simpul jaringan. Memahami tumpukan jaringan (Networking Stack) memungkinkan pengembang untuk membangun API yang efisien, mengelola koneksi konkuren yang masif (C10k problem), dan mengamankan transmisi data.

## 🏗️ The How (Arsitektur Internal)
Node.js menyediakan akses ke berbagai lapisan:
1.  **Net Module (TCP)**: Fondasi komunikasi berbasis aliran.
2.  **UDP/Dgram**: Komunikasi tanpa koneksi untuk kecepatan tinggi (game/streaming).
3.  **HTTP/HTTPS**: Protokol tingkat tinggi yang paling umum digunakan untuk Web.
4.  **HTTP/2 & QUIC**: Evolusi protokol untuk latensi rendah dan multiplexing.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: TCP/UDP Mastery**: Membangun protokol kustom yang andal dan cepat.
- **BK-02: HTTP Engine Internals**: Membedah bagaimana Node.js mengurai permintaan HTTP secara asinkron.
- **BK-03: DNS Resolving & Optimization**: Bagaimana alamat domain diterjemahkan menjadi IP.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Socket Hang-ups**: Koneksi yang terputus secara tidak terduga dapat menyebabkan kebocoran sumber daya jika tidak ditangani dengan event `error`.
- **Memory Pressure**: Penanganan koneksi yang tidak efisien dapat menyebabkan RAM membengkak karena buffer jaringan yang tidak terkelola.
- **Timeout Mismanagement**: Tanpa pengaturan timeout yang tepat, server bisa terjebak menunggu koneksi mati (zombie connections).
