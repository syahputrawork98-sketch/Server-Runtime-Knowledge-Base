# SR-05: Python Extending Node - The AI Interop

Membahas strategi integrasi antara Node.js dan Python, terutama untuk pemanfaatan ekosistem AI dan Data Science yang dominan di Python.

## 🎯 The Why (Visi Arsitektural)
Node.js unggul dalam I/O dan web, sementara Python raja di dunia Kecerdasan Buatan (AI) dan automasi data. Integrasi keduanya memungkinkan kita membangun aplikasi web yang ditenagai oleh model ML (Machine Learning) yang kuat tanpa harus memindahkan seluruh infrastruktur ke satu bahasa saja.

## 🏗️ The How (Arsitektur Internal)
Strategi integrasi yang umum digunakan:
1.  **Child Processes**: Menjalankan skrip Python sebagai proses terpisah dan berkomunikasi melalui STDIN/STDOUT.
2.  **Inter-Process Communication (IPC)**: Menggunakan Unix Sockets atau Pipes untuk pertukaran data yang lebih cepat.
3.  **Bridge Libraries (PyNode/Node-Py)**: Pustaka khusus yang mencoba memetakan objek antar kedua runtime secara lebih intim (seringkali melalui C++ bindings).
4.  **Microservices Pattern**: Komunikasi melalui HTTP/gRPC internal (seringkali cara paling stabil).

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Orchestrating Python Scripts**: Mengelola siklus hidup skrip AI Python dari Node.js.
- **BK-02: Fast Data Exchange with Streams**: Mengirimkan data sensor atau citra ke Python untuk diproses.
- **BK-03: Building Hybrid AI Apps**: Implementasi alur backend Node.js dengan otak pengelola model AI Python.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Startup Latency**: Menjalankan interpreter Python memiliki beban awal (startup cost) yang signifikan; hindari spawn proses baru untuk setiap request.
- **Data Serialization Bloat**: Mengonversi dataset besar menjadi teks (JSON) untuk dikirim ke Python sangat tidak efisien; gunakan format biner (seperti Protobuf atau Apache Arrow).
- **Environment Management**: Mengelola versi Python dan dependensi (`pip/venv`) secara paralel dengan `npm` menambah kompleksitas setup server.
