# SR-03: Advanced Protocols - Beyond HTTP/1.1

Membahas protokol komunikasi modern yang dirancang untuk efisiensi, real-time, dan arsitektur microservices yang kompleks.

## 🎯 The Why (Visi Arsitektural)
HTTP standar terkadang terlalu berat atau tidak efisien untuk interaksi antar-layanan (service-to-service). Protokol tingkat lanjut seperti gRPC atau MQTT menawarkan efisiensi biner dan latensi yang jauh lebih rendah, sangat krusial di era cloud-native dan IoT.

## 🏗️ The How (Arsitektur Internal)
Protokol modern yang didukung meliputi:
1.  **gRPC**: Komunikasi biner berbasis HTTP/2 dan Protocol Buffers.
2.  **WebSockets & Socket.io**: Standar emas untuk komunikasi real-time di server.
3.  **MQTT**: Protokol ringan untuk komunikasi hemat daya dan bandwidth (IoT).
4.  **GraphQL Internals**: Bagaimana mengelola skalabilitas query yang fleksibel di sisi server.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: gRPC for Microservices**: Implementasi kontrak layanan yang cepat dan andal.
- **BK-02: Scaling WebSockets**: Strategi mengelola jutaan koneksi real-time bersama-sama.
- **BK-03: Message Broker Interop (MQTT/AMQP)**: Komunikasi asinkron via RabbitMQ atau Mosquitto.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Complexity Overhead**: Menggunakan gRPC untuk aplikasi kecil hanya akan menambah kerumitan pengelolaan kontrak berkas `.proto`.
- **Binary Debugging Difficulty**: Data biner jauh lebih sulit dibaca oleh manusia dibandingkan JSON, memerlukan alat bantuan khusus untuk diagnosis.
- **Head-of-Line Blocking**: Meskipun HTTP/2 memperbaiki banyak hal, beberapa perilaku jaringan masih dapat menyebabkan kemacetan jika tidak dikonfigurasi dengan benar.
