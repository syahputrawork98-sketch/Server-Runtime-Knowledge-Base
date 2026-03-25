# Root Governance

Dokumen ini memuat aturan tingkat root untuk monorepo **Server Runtime Knowledge Base**.

## Prinsip Aturan Berjenjang

Aturan hanya berlaku **di level folder tempat aturan itu berada** dan **tidak mengatur isi yang lebih dalam**.

- **Root**: hanya mengatur isi di root.
- **Rak**: aturan hanya berlaku untuk isi di rak tersebut.
- **Sub-Rack (SR)**: kontainer utama untuk Buku (khusus RAK-02 hingga RAK-08).
- **Buku**: aturan hanya berlaku untuk isi di buku tersebut.

## Struktur Root

- `README.md` sebagai pendahuluan singkat
- `docs/` untuk dokumentasi pendukung
- `RAK-xx-.../` sebagai kumpulan rak (domain/tema)

## Konvensi Penomoran

- **Rak**: `RAK-01`, `RAK-02`, ...
- **Sub-Rack**: `SR-01`, `SR-02`, ... (Hanya untuk RAK-02 ke atas)
- **Buku**: `BK-01`, `BK-02`, ...
- **Bab**: `CH-01`, `CH-02`, ...

Kode tersebut digunakan untuk mempermudah diskusi dan penamaan folder.

## Ruang Lingkup Root

- Konvensi penamaan folder di root
- Struktur folder tingkat root
- Prinsip aturan berjenjang
- Konvensi penomoran

## Status

Aktif. Detail untuk rak/buku akan ditulis di README masing-masing.

## Rilis & Versi Buku

- Rilis dilakukan ketika pembuat merasa isi buku sudah cukup.
- Changelog hanya dicatat di buku tersebut.
- Format versi: Rxx-SRxx-BKxx-vN atau Rxx-BKxx-vN.

## Struktur Buku

Di level buku, struktur foldernya seperti ini:

- `README.md`
- `CHANGELOG.md`
- `docs/` (dokumen pendukung untuk buku ini)
- `CH-01-.../`, `CH-02-.../`, dst (bab; sejajar dengan `docs/`)

## Konvensi Penamaan Judul

- Judul rak dan buku memakai Title Case (contoh: Libuv Core).
- Judul bab boleh Title Case atau Kalimat Normal, tetapi konsisten di dalam satu buku.
- Bahasa judul: Indonesia (boleh pakai istilah teknis Inggris jika sudah umum).
