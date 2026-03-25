# Docs

Folder ini berisi seluruh dokumentasi lanjutan dan aturan monorepo untuk **Server Runtime Knowledge Base**.

## Konsep Monorepo (Analogi Perpustakaan)

- **Monorepo** = Perpustakaan
- **Rak** = Domain/tema besar
- **Sub-Rack (SR)** = Kategori spesifik di dalam rak (khusus RAK-02 ke atas)
- **Buku** = Modul/topik spesifik di dalam SR atau Rak

```mermaid
flowchart TB
    subgraph Library[Monorepo = Perpustakaan]
        R01[RAK-01: Anatomy]
        R02[RAK-02: Foundation]
        
        R01 --> BK1[BK-01: Market Share]
        R02 --> SR1[SR-01: Libuv Core]
        SR1 --> BK2[BK-01: Event Loop]
    end
```

## Pemetaan
- [mapping.md](file:///i:/Workspace/Workspace-Syahputrawork/02-Execution-Hubs/Server-Runtime-Knowledge-Base/docs/mapping.md)

## Tata Kelola
- [root-governance.md](file:///i:/Workspace/Workspace-Syahputrawork/02-Execution-Hubs/Server-Runtime-Knowledge-Base/docs/root-governance.md)

## Panduan Sumber Bab
- [chapter-sourcing.md](file:///i:/Workspace/Workspace-Syahputrawork/02-Execution-Hubs/Server-Runtime-Knowledge-Base/docs/chapter-sourcing.md)

## Referensi
- [references.md](file:///i:/Workspace/Workspace-Syahputrawork/02-Execution-Hubs/Server-Runtime-Knowledge-Base/docs/references.md)

## Pemetaan Referensi
- [reference-mapping.md](file:///i:/Workspace/Workspace-Syahputrawork/02-Execution-Hubs/Server-Runtime-Knowledge-Base/docs/reference-mapping.md)
