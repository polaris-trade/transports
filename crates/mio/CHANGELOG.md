# Changelog

All notable changes to this project will be documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)
and this project adheres to [Semantic Versioning](https://semver.org/).
## [0.3.2](https://github.com/polaris-trade/transports/compare/transport_mio-v0.4.0...transport_mio-v0.3.2) (2026-07-15)


### ⚠ BREAKING CHANGES

* **recv:** migrate mio backend to the owned-frame recv seam ([#10](https://github.com/polaris-trade/transports/issues/10))

### Features

* **mio:** implement transport_core::UdpTransport for MioTransport ([#6](https://github.com/polaris-trade/transports/issues/6)) ([1978fd7](https://github.com/polaris-trade/transports/commit/1978fd71a9008e8232bb503e756b76b3e7540b62))
* **recv:** migrate mio backend to the owned-frame recv seam ([#10](https://github.com/polaris-trade/transports/issues/10)) ([395222d](https://github.com/polaris-trade/transports/commit/395222d845abb2a6a21e259d371be914fc907804))
* **telemetry:** add recv-counter ([#19](https://github.com/polaris-trade/transports/issues/19)) ([b00fe53](https://github.com/polaris-trade/transports/commit/b00fe5366ceeeef1532c16a35fa11ad50b737bd8))
* **transport-mio:** added VecPool, UDP + TCP transports, MioTransport enum with poll_ready(timeout) ([#3](https://github.com/polaris-trade/transports/issues/3)) ([caa4e1f](https://github.com/polaris-trade/transports/commit/caa4e1fdb635dacbfad924dc0aa332c5a2f2f9c6))


### Bug fixes

* **mio:** probe socket before parking in ready() ([#17](https://github.com/polaris-trade/transports/issues/17)) ([b8f4c07](https://github.com/polaris-trade/transports/commit/b8f4c07b33c5222a57c393eed242f037a2cb1235))


### Refactor

* **lib:** restructure into single-crate layout ([#8](https://github.com/polaris-trade/transports/issues/8)) ([80a71e4](https://github.com/polaris-trade/transports/commit/80a71e46c9fbc71e20a0c50aab22c932ed9bbc91))


### Tests

* **bench:** add recv_burst throughput and allocation benchmark ([#13](https://github.com/polaris-trade/transports/issues/13)) ([e832b58](https://github.com/polaris-trade/transports/commit/e832b58e8421721750310126c143c76611bd2783))


### Build

* **deps:** re-tag criterion bump ([d13f7d5](https://github.com/polaris-trade/transports/commit/d13f7d5177c1e9a57e00d8dac9b7160176fb915c))
* **workspace:** merge transports workspace ([faa95b6](https://github.com/polaris-trade/transports/commit/faa95b68f16a6ce48fcef4c0459c0a45881ec40d))
* **workspace:** wire transports virtual workspace ([ff3a994](https://github.com/polaris-trade/transports/commit/ff3a994f67af771022adbc8898ce4cda0155def7))

## [0.4.0](https://github.com/polaris-trade/transport-mio/compare/transport_mio-v0.3.3...transport_mio-v0.4.0) (2026-07-11)


### Features

* **telemetry:** add recv-counter ([#19](https://github.com/polaris-trade/transport-mio/issues/19)) ([275ce73](https://github.com/polaris-trade/transport-mio/commit/275ce7308ac7d3afcd66ff68533d3d8b2e3f5188))

## [0.3.3](https://github.com/polaris-trade/transport-mio/compare/transport_mio-v0.3.2...transport_mio-v0.3.3) (2026-07-09)


### Bug fixes

* **mio:** probe socket before parking in ready() ([#17](https://github.com/polaris-trade/transport-mio/issues/17)) ([b6fe123](https://github.com/polaris-trade/transport-mio/commit/b6fe1237f06e63091933ffc2aafe915ce531a137))

## [0.3.2](https://github.com/polaris-trade/transport-mio/compare/transport_mio-v0.3.1...transport_mio-v0.3.2) (2026-07-09)


### Build

* **deps:** re-tag criterion bump ([df3ff4e](https://github.com/polaris-trade/transport-mio/commit/df3ff4edc001ce367f08a136f6be51446f88a43e))

## [0.3.1](https://github.com/polaris-trade/transport-mio/compare/transport_mio-v0.3.0...transport_mio-v0.3.1) (2026-07-09)


### Tests

* **bench:** add recv_burst throughput and allocation benchmark ([#13](https://github.com/polaris-trade/transport-mio/issues/13)) ([cf579a4](https://github.com/polaris-trade/transport-mio/commit/cf579a45dcf9ffd7ecf560b1ce79fd7ec7e4b009))

## [0.3.0](https://github.com/polaris-trade/transport-mio/compare/transport_mio-v0.2.1...transport_mio-v0.3.0) (2026-07-08)


### ⚠ BREAKING CHANGES

* **recv:** migrate mio backend to the owned-frame recv seam ([#10](https://github.com/polaris-trade/transport-mio/issues/10))

### Features

* **recv:** migrate mio backend to the owned-frame recv seam ([#10](https://github.com/polaris-trade/transport-mio/issues/10)) ([2250369](https://github.com/polaris-trade/transport-mio/commit/22503698e01872475b8846cc1b5ac0fb72b1d064))

## [0.2.1](https://github.com/polaris-trade/transport-mio/compare/transport_mio-v0.2.0...transport_mio-v0.2.1) - 2026-07-07

### Refactor

- *(lib)* Restructure into single-crate layout ([#8](https://github.com/polaris-trade/transport-mio/pull/8))


## [0.1.0](https://github.com/polaris-trade/transport-mio/releases/tag/transport_mio-v0.1.0) - 2026-07-04

### Features

- *(transport-mio)* Added VecPool, UDP + TCP transports, MioTransport enum with poll_ready(timeout) ([#3](https://github.com/polaris-trade/transport-mio/pull/3))


  Runtime-free backend for transport-core. Consumer drives mio::Poll via
MioTransport::poll_ready(timeout); poll_event and next_frame return from
the internal state populated by that call. UDP registers READABLE only
so the initial writable event does not spuriously wake poll_ready; TCP
registers READABLE|WRITABLE and drains the initial writable in
wait_connect so the same invariant holds post-connect. impl Transport
and impl TransportBind use async fn bodies that run sync work under the
covers, so tokio callers and hand-rolled executors both work.
