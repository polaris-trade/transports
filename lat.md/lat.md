# transports

Public Cargo workspace of the backend-agnostic recv seam (`transport_core`) plus two runtime backends that implement it. Every crate is zero-copy, batch-first, recv-first, and shares one recv contract.

`transport_core` owns the recv-seam traits, the `BufferPool` contract, config primitives, and the shared error; `transport_mio` and `transport_tokio` are two runtime bindings of that seam and depend on core by path, so a core change is one bump with no git-tag re-pin. Each crate has its own lat page.

- [[core]]: recv-seam traits, `BufferPool` contract, config primitives, shared error. No syscalls; every backend and protocol client depends on this crate only.
- [[mio]]: runtime-free mio backend, sync busy-poll UDP `DatagramSource` + TCP `StreamSource`, caller-driven recv thread.
- [[tokio]]: tokio backend, the same recv seam with an async readiness adapter over `tokio::net`.

## Miri

Pool ownership runs under the Miri interpreter to check the hand-written `unsafe impl Sync` and free-list invariants the compiler cannot verify statically.

The selection is both backends in one command: `cargo miri nextest run -p transport_tokio -p transport_mio --test pool`. Each backend's [[mio#Pool]] / [[tokio#Pool]] gates `UnsafeCell` slot access behind a `parking_lot` free list, with [[crates/mio/src/pool.rs#VecSlab]] / [[crates/tokio/src/pool.rs#VecSlab]] `Drop` returning the slot. The prime interpreter target is a `concurrent_acquire_drop_reclaims_full_capacity` test per crate: threads acquire a slab, write through the cell via `buf_mut`, and drop in-loop, so concurrent `Drop` free-list pushes race the reclaim path. Miri interprets those interleavings for slot aliasing and data races; the suite then asserts every slot returned by re-acquiring full capacity, proving reclaim converges, not merely that nothing panicked.

No pool test is Miri-excluded. The socket suites (`recv`, `tcp`, `conformance`, `rcvbuf`, readiness) live in separate test files and are never pulled in by `--test pool`, so no `#[cfg_attr(miri, ignore)]` is needed on the pool target. `parking_lot`'s lock internals emit a benign integer-to-pointer-cast provenance warning under Miri's strict default; the caller silences it with `-Zmiri-permissive-provenance` (does not affect the pass result).
