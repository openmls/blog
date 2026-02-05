---
title: "This month in OpenMLS #17 - January 2026"
date: 2026-02-05
tags: ["openmls", "this-month-in-openmls"]
notoc: true
author: "Franziskus Kiefer"
---

January 2026 brought steady progress (15 PRs merged) on robustness and APIs: dependency and CI updates, wasm bindings and API improvements, protocol feature additions (AppData mechanisms and GREASE handling), better TreeSync error handling and PSK checks, plus work to store pending proposals.

We also released two new versions of OpenMLS (technically in February on the 4th
not in January).

### v0.7.2

This release includes critical security patches addressing vulnerabilities
identified through external security research.
We recommend all users update to the latest version immediately.

The release does not contain breaking changes and should allow anyone on v0.7.1
to easily update.

#### Links

* [Github Release](https://github.com/openmls/openmls/releases/tag/openmls-v0.7.2)
* [Crate](https://crates.io/crates/openmls/0.7.2)

### v0.8.0

v0.8.0 is a regular release, including the critical fixes from v0.7.2, as well
as a significantly improved message validation and other changes.

#### New features
Extensions Draft 08 Support: Partial support for the [extensions-draft-08](https://datatracker.ietf.org/doc/html/draft-ietf-mls-extensions-08)
  behind the `extensions-draft-08` feature flag.
  This includes handling for AppEphemeral proposals, AppData mechanisms, and the
  forward secure exporter.

GREASE Support: Added handling and helper functions for GREASE (Generate Random Extensions And Sustain Extensibility) values to improve future protocol compatibility.

#### Links

* [Github Release](https://github.com/openmls/openmls/releases/tag/openmls-v0.8.0)
* [Crate](https://crates.io/crates/openmls/0.8.0)

### Merged PRs January 2026
* #1941: [Don't use git dependencies for hpke-rs, update tonic in interop_client](https://github.com/openmls/openmls/pull/1941)
* #1934: [add AAD getter to `PrivateMessageIn`](https://github.com/openmls/openmls/pull/1934)
* #1930: [Add AppData mechanisms from the extensions draft](https://github.com/openmls/openmls/pull/1930)
* #1928: [fix: check for duplicate PSK IDs in commits](https://github.com/openmls/openmls/pull/1928)
* #1927: [Enforce allowed extension types using Rust types](https://github.com/openmls/openmls/pull/1927)
* #1926: [Update rand dependency for `openmls` tests and `ds-lib` crate](https://github.com/openmls/openmls/pull/1926)
* #1924: [feat: make JoinBuilder::new API public](https://github.com/openmls/openmls/pull/1924)
* #1922: [chore(deps): update reqwest requirement from 0.12 to 0.13](https://github.com/openmls/openmls/pull/1922)
* #1921: [add to_bytes/from_bytes wasm bindings for KeyPackage/RatchetTree](https://github.com/openmls/openmls/pull/1921)
* #1917: [Fix typo in test comment for own messages](https://github.com/openmls/openmls/pull/1917)
* #1914: [ci update](https://github.com/openmls/openmls/pull/1914)
* #1912: [chore(deps): update criterion requirement from ^0.7 to ^0.8](https://github.com/openmls/openmls/pull/1912)
* #1903: [Improve the error return types in TreeSync](https://github.com/openmls/openmls/pull/1903)
* #1900: [Add handling and helpers for GREASE values](https://github.com/openmls/openmls/pull/1900)
* #1873: [feat: store pending proposals](https://github.com/openmls/openmls/pull/1873)

### Contributors
* [@erskingardner](https://github.com/erskingardner)
* [@mayel](https://github.com/mayel)
* [@franziskuskiefer](https://github.com/franziskuskiefer)
* [@dependabot[bot]](https://github.com/dependabot[bot])
* [@raphaelrobert](https://github.com/raphaelrobert)
* [@boxdot](https://github.com/boxdot)
* [@wysiwys](https://github.com/wysiwys)
* [@stanblock](https://github.com/stanblock)
* [@keks](https://github.com/keks)
* [@WaterWhisperer](https://github.com/WaterWhisperer)
* [@tbehner](https://github.com/tbehner)
* [@kkohbrok](https://github.com/kkohbrok)
* [@odama626](https://github.com/odama626)
