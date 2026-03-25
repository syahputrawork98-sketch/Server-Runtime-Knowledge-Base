# Pemetaan Knowledge Base (Server Runtime)

Pemetaan ini menyusun "rak" (domain/tema) dan "sub-rack" (kategori) untuk **Server Runtime Knowledge Base**.

## Rak Utama (8) dan Sub-Rack

1. **RAK-01 - Anatomy & Landscape** (Directly to Books)
   - BK-01: Runtime History & Evolution
   - BK-02: Ecosystem Landscape (Node vs Bun vs Deno)

2. **RAK-02 - Foundation & Core Rules**
   - SR-01: Libuv Core
   - SR-02: V8 Bindings
   - SR-03: Event Loop Phases

3. **RAK-03 - Evolution & Interfacing**
   - SR-01: Storage I/O
   - SR-02: Networking Stack
   - SR-03: Binary Data

4. **RAK-04 - Core Mechanics**
   - SR-01: Native Addons
   - SR-02: Threading Internals
   - SR-03: Server Memory

5. **RAK-05 - Ecosystem & Tooling**
   - SR-01: Module System
   - SR-02: Server Observability

6. **RAK-06 - The Underworld**
   - SR-01: OS Intersection
   - SR-02: Parallelism Patterns

7. **RAK-07 - Specialization & Edge**
   - SR-01: Stream Mastery
   - SR-02: Secure Runtime
   - SR-03: Advanced Protocols

8. **RAK-08 - Matrix Intersection**
   - SR-01: JS Node Orchestration
   - SR-02: TS Transpilation Runtime
   - SR-03: Rust NAPI Addons
   - SR-04: Go CShared Bindings
   - SR-05: Python Extending Node

## Relasi Lintas Rak

Setiap modul berinteraksi lintas rak (mis. Native Addons di RAK-04 berhubungan erat dengan Matrix Intersection di RAK-08).
