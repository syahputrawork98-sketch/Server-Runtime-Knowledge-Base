# Konvensi Penamaan & Struktur Folder (Server Runtime Edition)

## 1. Penamaan Direktori
| Level | Prefix | Format | Contoh |
| :--- | :--- | :--- | :--- |
| **Rak** | `RAK-` | `RAK-XX-slug` | `RAK-02-foundation` |
| **Sub-Rak** | `SR-` | `SR-01-libuv` | `SR-01-libuv` |
| **Buku** | `BK-` | `BK-XX_Slug` | `BK-01_EventLoop` |
| **Bab** | `CH-` | `CH-XX_Slug` | `CH-01_Phases` |
| **Section** | `SEC-` | `SEC-XX_Slug` | `SEC-01_Poll` |

---

## 2. Struktur Internal Unit
```text
CH- atau SEC-/
├── README.md        <- Materi inti.
├── examples/        <- Kode lab (.js).
└── assets/          <- Media statis.
```

## 3. Aturan Lab Praktis (`examples/`)
File wajib menggunakan prefix numerik: `01_tcp_server.js`, `02_event_emitter.js`.
