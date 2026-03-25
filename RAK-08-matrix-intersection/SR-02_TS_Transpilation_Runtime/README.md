# SR-02: TS Transpilation Runtime - Type-Safe Server

Membahas berbagai strategi menjalankan TypeScript di sisi server, mulai dari transpilasi manual hingga runtime modern yang mendukung TS secara native.

## 🎯 The Why (Visi Arsitektural)
TypeScript di server memberikan keamanan kontrak data (API) yang sangat berharga bagi tim besar. Namun, karena server memiliki siklus hidup yang lebih lama dari browser, pilihan strategi eksekusi (JIT vs AOT transpilasi) berdampak langsung pada kecepatan startup dan pemeliharaan jangka panjang.

## 🏗️ The How (Arsitektur Internal)
Opsi eksekusi meliputi:
1.  **AOT (Ahead-of-Time)**: Mengompilasi TS menjadi JS sebelum dijalankan (standard cara profesional/production).
2.  **JIT Transpilation (ts-node)**: Menghapus tipe data saat runtime sebelum dikirim ke V8 (populer untuk development).
3.  **Modern Runtimes (Bun/Deno)**: Runtime yang secara internal dapat langsung memproses berkas `.ts` tanpa langkah transpilasi eksternal yang terlihat.

## 🧪 The Practical (Roadmap Buku)
- **BK-01: Production Build Pipelines**: Membangun workflow `tsc` + `swc` untuk performa kompilasi kilat.
- **BK-02: Decorators & Server-side Metadata**: Penggunaan TS untuk arsitektur berorientasi objek (seperti NestJS).
- **BK-03: Type-safe Environment Variables**: Menjamin konfigurasi server sesuai kontrak data sejak startup.

## ⚠️ The Pitfalls (Batas & Kerentanan)
- **The "Compile Delay" Gap**: Proses kompilasi yang lambat pada proyek raksasa dapat merusak pengalaman pengembangan harian.
- **Reflection Limitations**: TypeScript hanya ada di level kompilasi; akses metadata saat runtime memerlukan pustaka tambahan yang menambah beban memori.
- **Missing Type Safety at IO Boundaries**: TypeScript tidak bisa menjamin validitas data yang datang dari database atau permintaan HTTP tanpa skema validasi runtime (Zod/ArkType).
