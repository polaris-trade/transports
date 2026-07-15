# transports

**Visibility: PUBLIC (OSS). Licensed `MIT OR Apache-2.0`.** A single Cargo virtual workspace holding the backend-agnostic recv seam (`transport_core`) and two runtime backends that implement it.

Every crate is zero-copy, batch-first, and recv-first, and shares one recv contract. `transport_core` owns the traits, the `BufferPool` contract, config primitives, and the shared error type; the two backends are runtime bindings of that seam. The backends depend on core **by path**, so a core change is one bump with no git-tag re-pin hop between them.

## Crates

| Crate | Path | Version | Role |
|---|---|---|---|
| `transport_core` | `crates/core` | 0.4.0 | Recv-seam traits, `BufferPool` contract, config, shared error. No syscalls; every backend and protocol client depends on this crate only. |
| `transport_mio` | `crates/mio` | 0.4.0 | Runtime-free mio backend: sync busy-poll UDP `DatagramSource` + TCP `StreamSource`, caller-driven recv thread. |
| `transport_tokio` | `crates/tokio` | 0.4.0 | Tokio backend: the same recv seam with an async readiness adapter over `tokio::net`. |

`workspace-hack` is an internal hakari crate for feature unification; it is never released.

## Dependencies

`transport_mio` and `transport_tokio` depend on `transport_core` as an in-workspace path dependency (`features = ["observability"]`). `observability` is a public git-tag dev-dependency. There is no dependency on any private crate.

## Tags and releases

Each crate releases on its own per-crate tag: `transport_core-vX.Y.Z`, `transport_mio-vX.Y.Z`, `transport_tokio-vX.Y.Z`. release-please drives the bumps; `publish = false` (git-tag distribution, no crates.io).

## Pinning: same-tag rule

A consumer that pulls **two or more** crates from this repo (for example `transport_core` **and** `transport_tokio`) must pin them all to the **same tag**. Cargo keys a git source by `(url, tag)`, so two crates from this one repo at two different tags resolve to two separate checkouts and duplicate `transport_core`, which fails to compile with `E0308`. Pick one tag whose commit carries every crate version you need and pin all of them to that same tag. A consumer pulling a single crate is unaffected.

## License

Dual-licensed under either of `MIT OR Apache-2.0` at your option. Each crate carries its own `LICENSE-MIT`, `LICENSE-APACHE`, and `NOTICE`.
