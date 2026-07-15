# transports

Public Cargo workspace of the backend-agnostic recv seam (`transport_core`) plus two runtime backends that implement it. Every crate is zero-copy, batch-first, recv-first, and shares one recv contract.

`transport_core` owns the recv-seam traits, the `BufferPool` contract, config primitives, and the shared error; `transport_mio` and `transport_tokio` are two runtime bindings of that seam and depend on core by path, so a core change is one bump with no git-tag re-pin. Each crate has its own lat page.

- [[core]]: recv-seam traits, `BufferPool` contract, config primitives, shared error. No syscalls; every backend and protocol client depends on this crate only.
- [[mio]]: runtime-free mio backend, sync busy-poll UDP `DatagramSource` + TCP `StreamSource`, caller-driven recv thread.
- [[tokio]]: tokio backend, the same recv seam with an async readiness adapter over `tokio::net`.
