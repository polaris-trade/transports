# Changelog

All notable changes to this project will be documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)
and this project adheres to [Semantic Versioning](https://semver.org/).
## [0.3.2](https://github.com/polaris-trade/transports/compare/transport_tokio-v0.4.0...transport_tokio-v0.3.2) (2026-07-15)


### ⚠ BREAKING CHANGES

* **recv:** Transport/TokioFrame/TokioEvent/TcpFrame and the RecvBatch recvmmsg helpers are gone; construct via TransportBind and consume frames through DatagramSource/StreamSource.

### Features

* **ci:** update deps registry ([#5](https://github.com/polaris-trade/transports/issues/5)) ([e1ba5d7](https://github.com/polaris-trade/transports/commit/e1ba5d7d22cda31c093793a9cc7014fc3056c29c))
* **recv:** migrate tokio backend to the owned-frame recv seam ([#10](https://github.com/polaris-trade/transports/issues/10)) ([0ca0907](https://github.com/polaris-trade/transports/commit/0ca0907be33a7f2f85d6a59ddff807e3816ff8b7))
* **telemetry:** add recv-counter ([#22](https://github.com/polaris-trade/transports/issues/22)) ([5395b58](https://github.com/polaris-trade/transports/commit/5395b5855cde83f0e42c17629416718af9eb3a5f))
* **tokio:** implement transport_core::UdpTransport for TokioTransport ([#4](https://github.com/polaris-trade/transports/issues/4)) ([35a2a7c](https://github.com/polaris-trade/transports/commit/35a2a7c40f045b8b0bf24de27bed29482a790a7e))
* **transport-tokio:** add VecPool, UDP + TCP transports, and Linux recvmmsg batching ([#1](https://github.com/polaris-trade/transports/issues/1)) ([8bdf0cd](https://github.com/polaris-trade/transports/commit/8bdf0cd32e8e8104c98902e539bededf019074fb))


### Bug fixes

* **tokio:** clear stale reactor readiness before async recv wait ([#18](https://github.com/polaris-trade/transports/issues/18)) ([e128021](https://github.com/polaris-trade/transports/commit/e128021db7818a917915dee5ef15699e57f0905e))


### Refactor

* **lib:** restructure into single-crate layout ([#8](https://github.com/polaris-trade/transports/issues/8)) ([dc2795b](https://github.com/polaris-trade/transports/commit/dc2795be318b3b580db743f9a3acf0936ea01cd7))


### Tests

* **bench:** add recv_burst throughput and allocation benchmark ([#14](https://github.com/polaris-trade/transports/issues/14)) ([7cc365a](https://github.com/polaris-trade/transports/commit/7cc365a0a149430e4d39d2e02d8cf2d0500a122c))


### Build

* **deps:** bump criterion to 0.8.2 ([#16](https://github.com/polaris-trade/transports/issues/16)) ([165e917](https://github.com/polaris-trade/transports/commit/165e917e08da13598c9b0b7089497e45f6dadc08))
* **deps:** bump transport-core to v0.3.2 ([#20](https://github.com/polaris-trade/transports/issues/20)) ([095aadd](https://github.com/polaris-trade/transports/commit/095aadd0257ce43eff69616789763e03390db46a))
* **deps:** re-tag criterion bump ([d13f7d5](https://github.com/polaris-trade/transports/commit/d13f7d5177c1e9a57e00d8dac9b7160176fb915c))
* **workspace:** wire transports virtual workspace ([ff3a994](https://github.com/polaris-trade/transports/commit/ff3a994f67af771022adbc8898ce4cda0155def7))

## [0.4.0](https://github.com/polaris-trade/transport-tokio/compare/transport_tokio-v0.3.4...transport_tokio-v0.4.0) (2026-07-11)


### Features

* **telemetry:** add recv-counter ([#22](https://github.com/polaris-trade/transport-tokio/issues/22)) ([1445c75](https://github.com/polaris-trade/transport-tokio/commit/1445c75a7f0a48679c36011cbb84ffe6404d2dac))

## [0.3.4](https://github.com/polaris-trade/transport-tokio/compare/transport_tokio-v0.3.3...transport_tokio-v0.3.4) (2026-07-09)


### Build

* **deps:** bump transport-core to v0.3.2 ([#20](https://github.com/polaris-trade/transport-tokio/issues/20)) ([505b147](https://github.com/polaris-trade/transport-tokio/commit/505b147f44d4f647d1f8a2c997cdeafd2f4392ad))

## [0.3.3](https://github.com/polaris-trade/transport-tokio/compare/transport_tokio-v0.3.2...transport_tokio-v0.3.3) (2026-07-09)


### Bug fixes

* **tokio:** clear stale reactor readiness before async recv wait ([#18](https://github.com/polaris-trade/transport-tokio/issues/18)) ([9b98f06](https://github.com/polaris-trade/transport-tokio/commit/9b98f062733e4d6cb743ad008c6ded54f2509905))

## [0.3.2](https://github.com/polaris-trade/transport-tokio/compare/transport_tokio-v0.3.1...transport_tokio-v0.3.2) (2026-07-09)


### Build

* **deps:** bump criterion to 0.8.2 ([#16](https://github.com/polaris-trade/transport-tokio/issues/16)) ([1f81594](https://github.com/polaris-trade/transport-tokio/commit/1f81594703548378533f9471004f989c912c1d6a))

## [0.3.1](https://github.com/polaris-trade/transport-tokio/compare/transport_tokio-v0.3.0...transport_tokio-v0.3.1) (2026-07-09)


### Tests

* **bench:** add recv_burst throughput and allocation benchmark ([#14](https://github.com/polaris-trade/transport-tokio/issues/14)) ([acfb116](https://github.com/polaris-trade/transport-tokio/commit/acfb116abadcb266a5c4588808dccd64949180f2))

## [0.3.0](https://github.com/polaris-trade/transport-tokio/compare/transport_tokio-v0.2.1...transport_tokio-v0.3.0) (2026-07-08)


### ⚠ BREAKING CHANGES

* **recv:** Transport/TokioFrame/TokioEvent/TcpFrame and the RecvBatch recvmmsg helpers are gone; construct via TransportBind and consume frames through DatagramSource/StreamSource.

### Features

* **recv:** migrate tokio backend to the owned-frame recv seam ([#10](https://github.com/polaris-trade/transport-tokio/issues/10)) ([40bdb87](https://github.com/polaris-trade/transport-tokio/commit/40bdb8783f8fd2e106e0eb25791382a879c37c73))

## [0.2.1](https://github.com/polaris-trade/transport-tokio/compare/transport_tokio-v0.2.0...transport_tokio-v0.2.1) - 2026-07-07

### Refactor

- *(lib)* Restructure into single-crate layout ([#8](https://github.com/polaris-trade/transport-tokio/pull/8))


## [0.1.0](https://github.com/polaris-trade/transport-tokio/releases/tag/transport_tokio-v0.1.0) - 2026-07-04

### Features

- *(transport-tokio)* Add VecPool, UDP + TCP transports, and Linux recvmmsg batching ([#1](https://github.com/polaris-trade/transport-tokio/pull/1))


  First functional layer of the tokio backend for transport_core.

Pool:
- VecPool + SharedVecPool: bounded slab pool with UnsafeCell<Vec<u8>> slots gated by a parking_lot::Mutex<Vec<u32>> free list.
- VecSlab::drop returns the slot; SharedVecPool newtype satisfies the orphan rule for impl BufferPool.

UDP:
- UdpTransport wraps tokio::net::UdpSocket. apply_socket_opts installs SO_REUSEADDR, SO_REUSEPORT (unix), SO_RCVBUF, SO_SNDBUF, and SO_BUSY_POLL (Linux via libc::setsockopt).
- Kernel shortfalls and unsupported knobs emit tracing::warn! instead of failing bind.
- so_timestamping requests currently warn since the recvmsg ancillary-data path is not yet wired; lands with recvmmsg batching in a follow-up.
- Linux-only recv_batch_linux drains a burst via libc::recvmmsg, gated behind tokio's readable().await + try_io. Preallocated RecvBatch owns per-slot buffers, iovs, addrs, and cmsg storage so hot loops do not reallocate.

TCP:
- TcpTransport wraps tokio::net::TcpStream. connect opens the stream to BindConfig::addr (interpreted as the remote peer) and applies SO_RCVBUF / SO_SNDBUF via socket2::SockRef.
- poll_recv reads one chunk per poll; zero-byte reads surface as UnexpectedEof so callers can react to peer close.
- TCP is stream-oriented, so TcpFrame carries opaque bytes and the protocol crate handles framing.

Surface:
- TokioTransport enum dispatches Transport + TransportBind across the Udp and Tcp variants.
- TokioFrame mirrors the split; TokioEvent carries SocketAddr for UDP and byte count for TCP.

Stats:
- ReceiverStats holds atomic kernel_drops, packets_recv, bytes_recv counters shared via Arc; snapshot() returns a plain read-only copy for observability polling.
- apply_socket_opts installs SO_RXQ_OVFL on Linux when RecvBufConfig::so_rxq_ovfl is set; each recv carries the cumulative kernel-drop count in ancillary data.
- parse_scm_rxq_ovfl walks the cmsg list; the highest value seen in a batch advances kernel_drops monotonically via CAS.

Tests:
- Pool accounting under contention (drop reclaim, exhaustion, oversize rejection, 8-thread concurrent acquire).
- SO_RCVBUF loopback bind smoke.
- Loopback TCP echo through send / poll_event / next_frame.
- transport_core::testing::run_conformance_suite asserts BindUdp, ConnectTcp (via the suite's auto-spun peer), NameNonEmpty.
- recvmmsg.rs verifies burst batches >= 2 datagrams end-to-end.
- drops.rs (#[ignore]) floods rcvbuf and asserts non-zero kernel_drops.
