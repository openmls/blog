---
title: "This month in OpenMLS #11 - July 2025"
date: 2025-08-01
tags: ["openmls", "this-month-in-openmls"]
notoc: true
author: "Franziskus Kiefer"
---

We merged 16 PRs in July with fixes to documentation and code improvements, and
most importantly, [OpenMLS v0.7](https://github.com/openmls/openmls/releases/tag/openmls-v0.7.0)
got released 🎉.

Important fixes that got merged in July are [#1797](https://github.com/openmls/openmls/pull/1797),
which ensures that the ratchet tree is trimmed correctly after processing proposals,
and [#1793](https://github.com/openmls/openmls/pull/1793), which
corrects the calculation of the free index when inserting a new leaf node into
the ratchet tree in certain cases.
OpenMLS now also supports `GroupContextExtensions` in external proposals.

### Merged PRs July 2025
* #1816: [Fix doc comment on `LeafNode::credential()`](https://github.com/openmls/openmls/pull/1816)
* #1813: [Update CHANGELOG.md](https://github.com/openmls/openmls/pull/1813)
* #1809: [fix(doc): `SqliteStorageProvider` database initialization](https://github.com/openmls/openmls/pull/1809)
* #1807: [feat: set migration table name for refinery migrations](https://github.com/openmls/openmls/pull/1807)
* #1806: [Bump packages to full (non-pre) versions](https://github.com/openmls/openmls/pull/1806)
* #1805: [Bump openmls and openmls_test to -pre.2](https://github.com/openmls/openmls/pull/1805)
* #1802: [export `mls_group::builder::*`](https://github.com/openmls/openmls/pull/1802)
* #1800: [Update clippy.yml](https://github.com/openmls/openmls/pull/1800)
* #1798: [Bump all the versions to the next -pre.1](https://github.com/openmls/openmls/pull/1798)
* #1797: [fix: trim diff tree after processing all proposals](https://github.com/openmls/openmls/pull/1797)
* #1796: [Update changelog](https://github.com/openmls/openmls/pull/1796)
* #1795: [Documentation fixes and pub use `commit_builder::*` ](https://github.com/openmls/openmls/pull/1795)
* #1793: [fix: SelfRemove proposal type and free index calculation](https://github.com/openmls/openmls/pull/1793)
* #1791: [Update hpke-rs and libcrux dependencies to 0.3.0](https://github.com/openmls/openmls/pull/1791)
* #1790: [fix `uninlined_format_args` lint](https://github.com/openmls/openmls/pull/1790)
* #1784: [Support GroupContextExtensions proposals from external senders](https://github.com/openmls/openmls/pull/1784)

### Contributors
* [@wysiwys](https://github.com/wysiwys)
* [@franziskuskiefer](https://github.com/franziskuskiefer)
* [@kkohbrok](https://github.com/kkohbrok)
* [@ppiotr3k](https://github.com/ppiotr3k)
* [@SimonThormeyer](https://github.com/SimonThormeyer)
* [@keks](https://github.com/keks)
