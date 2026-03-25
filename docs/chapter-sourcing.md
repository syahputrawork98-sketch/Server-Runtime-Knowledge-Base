# Aturan Pengambilan Bab dari Referensi

Bab di dalam repositori ini **diambil dari buku besar atau dokumen referensi resmi** yang relevan, lalu dipindahkan/dipecah sesuai pengelompokan rak dan buku.

## Prinsip Utama

- Struktur bab **mengikuti referensi** (tidak dipaksa oleh struktur buatan).
- Semua bab dari referensi **boleh dimasukkan**.
- Repositori **terus berkembang** mengikuti update referensi.

## Penomoran Bab

- Kode bab: `CH-01`, `CH-02`, `CH-03`, ...
- Nama folder bab memakai `snake_case` atau `kebab-case` dengan awalan kode (contoh: `CH-01_event_loop`).

## Lokasi Bab

Folder bab berada di root folder buku (sejajar dengan `docs/`) dengan pola `CH-01-...`, `CH-02-...`, dst.

## Metadata Wajib per Bab

Setiap bab harus mencatat:
- Sumber referensi (judul dokumen/buku besar)
- Versi atau tanggal rilis referensi
- Lokasi bab di referensi (misalnya bab/section)

## Isi Minimum Bab

Setiap bab minimal berisi:
- Ringkasan
- Tujuan
- Alur utama (langkah-langkah)
- Istilah kunci
- Sumber referensi (dengan versi/tanggal)

## Struktur Folder Bab

Di dalam folder bab:
- `README.md` (isi utama bab)
- `docs/` (penjelasan pendukung untuk `README.md`)
- `assets/` (gambar, SVG)
- `examples/` (contoh kode/skenario)

## Aturan SVG

- SVG dibuat terakhir setelah konten teks stabil.
- Diagram harus relevan dengan isi bab spesifik.
