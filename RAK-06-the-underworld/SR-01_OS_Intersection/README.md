# SR-01: OS Intersection - The POSIX & System Layers

Membahas interaksi tingkat rendah antara Node.js dengan inti Sistem Operasi (Kernel) melalui abstraksi POSIX dan sistem pemanggilan file/proses.

## 🎯 The Why (Visi Arsitektural)
Server Runtime bukan sekadar interpreter bahasa, melainkan jembatan ke mesin fisik. Memahami bagaimana Node.js berinteraksi dengan OS (melalui System Calls) memungkinkan pengembang menulis kode yang efisien, aman, dan kompatibel dengan lingkungan cloud/enterprise yang ketat.

## 🏗️ The How (Arsitektur Internal)
Interaksi ini dikelola melalui beberapa saluran:
1.  **System Calls (syscalls)**: Permintaan langsung ke Kernel untuk operasi file, jaringan, atau manajemen proses.
2.  **POSIX Standards**: Kepatuhan Node.js terhadap standar UNIX untuk portabilitas lintas Linux/macOS.
3.  **Signals**: Mekanisme komunikasi antar proses (misal: `SIGTERM`, `SIGKILL`) untuk manajemen siklus hidup aplikasi.
4.  **Pipes & Streams**: Berbagi data antar proses OS melalui standar Input/Output (STDIN/STDOUT).

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Handling OS Signals**: Membangun aplikasi "Graceful Shutdown" yang bersih.
- **BK-02: Working with Pipes & TTY**: Mengelola aliran data antar proses baris perintah (CLI).
- **BK-03: Process IDs & Permissions**: Mengelola hak akses dan identitas proses pada server multiuser.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **Zombie Processes**: Gagal membersihkan proses anak (child processes) dapat menghabiskan tabel proses OS.
- **Windows vs POSIX Discrepancy**: Banyak fitur sistem (seperti sinyal atau permission file) berperilaku berbeda di Windows dibanding Linux.
- **Signal Safety**: Menangani sinyal secara tidak tepat dapat menyebabkan crash pada operasi asinkron yang sedang berjalan.
