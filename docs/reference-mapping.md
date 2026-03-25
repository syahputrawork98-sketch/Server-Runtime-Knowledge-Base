# Pemetaan Referensi ke Buku (Server Runtime)

Dokumen ini memetakan referensi induk ke rak dan buku untuk menjaga silsilah informasi.

## RAK-02 - Foundation & Core Rules

- **SR-01 (Libuv Core)**: Libuv Documentation.
- **SR-02 (V8 Bindings)**: V8 Embedder's Guide + Node.js Source (src/node_v8.cc).
- **SR-03 (Event Loop Phases)**: Node.js Docs (Event Loop, Timers, and nextTick).

## RAK-03 - Evolution & Interfacing

- **SR-01 (Storage I/O)**: Node.js `fs` module docs + POSIX File System specs.
- **SR-02 (Networking Stack)**: Node.js `net` & `http` docs + RFC 9110/9112.
- **SR-03 (Binary Data)**: Node.js `buffer` docs + ECMAScript `TypedArray`.

## RAK-04 - Core Mechanics

- **SR-01 (Native Addons)**: Node-API Documentation.
- **SR-02 (Threading Internals)**: Node.js `worker_threads` docs + Libuv Thread Pool guides.
- **SR-03 (Server Memory)**: V8 Memory Management docs + Node.js memory profiling guides.

## RAK-07 - Specialization & Edge

- **SR-01 (Stream Mastery)**: Node.js `stream` module docs.
- **SR-02 (Secure Runtime)**: Node.js `crypto` & `tls` docs + OWASP Node.js Cheat Sheet.
- **SR-03 (Advanced Protocols)**: gRPC docs + MQTT spec + HTTP/2 RFC.

## RAK-08 - Matrix Intersection

- **SR-02 (TS Runtime)**: TypeScript Handbook + ts-node/swc docs.
- **SR-03 (Rust NAPI)**: napi.rs documentation.
- **SR-04 (Go CShared)**: Go `cgo` documentation.
- **SR-05 (Python Interop)**: Node.js `child_process` docs + Pyodide/Bridge docs.
