# SR-02: Server Observability - Monitoring at Scale

Membahas cara memantau kesehatan server, melacak kesalahan, dan menganalisis performa pada sistem yang berjalan di lingkungan produksi.

## 🎯 The Why (Visi Arsitektural)
Server yang sedang berjalan adalah "kotak hitam" tanpa observabilitas. Di lingkungan produksi, kita tidak memiliki akses langsung (Console) seperti di browser. Observabilitas memungkinkan tim operasional mengetahui masalah *sebelum* pengguna melaporkannya.

## 🏗️ The How (Arsitektur Internal)
Observabilitas server dibangun di atas tiga pilar utama:
1.  **Logging**: Mencatat kejadian diskrit (Errors, Info) untuk audit dan debug masa lalu.
2.  **Metrics**: Data numerik (CPU, Memory, Request rate) untuk melihat tren performa secara real-time.
3.  **Tracing**: Melacak jalur permintaan tunggal melintasi berbagai layanan asinkron (Distributed Tracing).

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Structured Logging Patterns**: Menggunakan JSON logging untuk integrasi dengan sistem ELK/Splunk.
- **BK-02: Prometheus & Grafana Integration**: Membangun dashboard kesehatan server yang visual.
- **BK-03: Distributed Tracing with OpenTelemetry**: Melacak latensi dari entry point hingga database.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Log Overflow**: Mencatat terlalu banyak informasi (Verbose) dapat memenuhi kapasitas disk dan memperlambat performa server karena konsumsi I/O.
- **Sensitive Data Leakage**: Tanpa filter yang ketat, log seringkali tidak sengaja menyimpan rahasia seperti Password atau Token JWT.
- **Monitoring Blindspots**: Memantau metrik yang salah dapat memberikan rasa aman palsu sementara sistem sebenarnya sedang gagal secara internal.
