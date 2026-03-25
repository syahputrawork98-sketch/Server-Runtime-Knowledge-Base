# Arsitektur & Hierarki Struktur (Server Runtime Edition)

Proyek **Server Runtime Knowledge Base** disusun dengan standar **Unified Gold Standard (PPM V4)**.

## 1. Hirarki 6-Level
| Tingkatan | Nama | Prefix | Contoh |
| :--- | :--- | :--- | :--- |
| **Level 1** | **Root** | `/` | `/` |
| **Level 2** | **Rak** | `RAK-` | `RAK-01-anatomy/` |
| **Level 3** | **Sub-Rak** | `SR-` | `SR-01-libuv/` |
| **Level 4** | **Buku** | `BK-` | `BK-01_EventLoop/` |
| **Level 5** | **Bab** | `CH-` | `CH-01_Phases/` |
| **Level 6** | **Section** | `SEC-` | `SEC-01_PollPhase/` |

---

## 2. Karakteristik 8-RAK Architecture
*Struktur ini dirancang untuk menampung **5 Bahasa Utama (JS, TS, Rust, Go, Python)** dalam ekosistem Server.*

1. **RAK-01-anatomy**: Sejarah Node.js & Filosofi I/O.
2. **RAK-02-foundation**: Libuv, V8 Bindings, & Event Loop Phases.
3. **RAK-03-evolution**: Node APIs: FS, Net, Http, Buffer.
4. **RAK-04-core-mechanics**: C++ Addons, Thread Pool, & Memory.
5. **RAK-05-ecosystem**: NPM, Debuggers, & Profiling.
6. **RAK-06-the-underworld**: POSIX I/O, System Calls, & Cluster.
7. **RAK-07-specialization**: Streams, Crypto, & Advanced Network.
8. **RAK-08-matrix-intersection**: The Bridge Between Languages & Server.

---

## 3. Kriteria Gold Standard
Setiap unit materi (CH/SEC) wajib memiliki:
1. **Source Link** (Akurasi Node.js Docs / Libuv / Linux Man Pages).
2. **Dual Definition** (Formal + Model Mental).
3. **Mermaid Diagram**.
4. **Mekanisme Detil** (C++ level).
5. **Lab Praktis** (Relasi ke kode `.js` / `.cc` di `examples/`).
