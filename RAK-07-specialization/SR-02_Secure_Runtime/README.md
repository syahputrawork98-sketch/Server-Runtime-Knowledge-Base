# SR-02: Secure Runtime - Hardening the Server

Membahas strategi keamanan di tingkat runtime untuk melindungi server dari serangan siber dan mengelola data rahasia.

## 🎯 The Why (Visi Arsitektural)
Server adalah target utama serangan. Kebocoran data atau eksekusi kode jarak jauh (RCE) dapat menghancurkan bisnis. Secure Runtime memastikan kode berjalan di dalam zirah pelindung, meminimalkan permukaan serangan melalui enkripsi dan praktik keamanan terbaik.

## 🏗️ The How (Arsitektur Internal)
Keamanan di Node.js mencakup lapisan:
1.  **Crypto Module**: Akses ke algoritma kriptografi canggih (OpenSSL internal).
2.  **TLS/SSL**: Komunikasi terenkripsi tingkat tinggi untuk jaringan.
3.  **Permission Models**: Pembatasan akses ke file system atau jaringan (terutama pada runtime modern seperti Deno/Bun, namun dapat disimulasikan di Node).
4.  **Security Advisories Audit**: Proses auditing dependensi pihak ketiga secara otomatis (`npm audit`).

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Encryption & Hashing Patterns**: Strategi mengamankan password dan data sensitif di database.
- **BK-02: TLS & Certificate Management**: Implementasi HTTPS dan mTLS (Mutual TLS).
- **BK-03: OWASP Top 10 for Node.js**: Praktik pertahanan spesifik untuk mencegah injeksi dan serangan token.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Weak Crypto Algorithms**: Menggunakan algoritma lama (seperti MD5 atau SHA-1) memberikan rasa aman palsu.
- **Unsafe Eval/New Function**: Mengeksekusi string sebagai kode JavaScript adalah pintu masuk utama untuk serangan injeksi kode.
- **Supply Chain Attacks**: Terlalu percaya pada dependensi `node_modules` tanpa verifikasi atau audit rutin.
