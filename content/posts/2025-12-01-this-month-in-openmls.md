---
title: "This month in OpenMLS #15 - November 2025"
date: 2025-12-01
tags: ["openmls", "this-month-in-openmls"]
notoc: true
author: "Franziskus Kiefer"
---

We merged 22 PRs in November.

### New Features and Fixes 🚀

We added a couple features from the MLS exntesions draft.
- OpenMLS now supports safe HPKE encrypt/decrypt with label, allowing applications to safely encrypt to public keys.
- It also supports the AppEphemeral proposal.
- The AppAck handling was updated in line with the extensions draft.
- Other parts of the supporting crates got updated to work with the features from the extensions draft.

All features from the extensions draft are behind the `extensions-draft-08` for now.

Other changes include:
- Optimized `Signable` to reuse serialized payloads, reducing allocations and improving performance in signing paths.
- Added AES-GCM support to the `libcrux` provider.
- Miscellaneous CI and docs/fmt fixes: removed nightly-only `cargo fmt` config, fixed rustdoc links, and bumped several GH Actions and dependency versions.

### Merged PRs November 2025
* #1909: [Remove nightly-only `cargo fmt` config settings](https://github.com/openmls/openmls/pull/1909)
* #1908: [fixup: rustdoc links](https://github.com/openmls/openmls/pull/1908)
* #1907: [ci: remove crypto-subtle feature from cargo hack](https://github.com/openmls/openmls/pull/1907)
* #1906: [book: remove multilingual config](https://github.com/openmls/openmls/pull/1906)
* #1902: [chore(deps): bump actions/checkout from 5 to 6](https://github.com/openmls/openmls/pull/1902)
* #1901: [feat: optimize Signable to reuse serialized payload](https://github.com/openmls/openmls/pull/1901)
* #1898: [Implement HPKE safe encrypt/decrypt with label (MLS Extensions Draft)](https://github.com/openmls/openmls/pull/1898)
* #1894: [[CI] Build workspace with `extensions-draft-08` feature flag, and simplify `openmls` crate feature build combinations](https://github.com/openmls/openmls/pull/1894)
* #1892: [chore(deps): update thiserror requirement from 1.0 to 2.0](https://github.com/openmls/openmls/pull/1892)
* #1891: [chore(deps): update indicatif requirement from 0.17.8 to 0.18.3](https://github.com/openmls/openmls/pull/1891)
* #1888: [chore(deps): update refinery requirement from 0.8 to 0.9](https://github.com/openmls/openmls/pull/1888)
* #1881: [chore(deps): update criterion requirement from ^0.5 to ^0.7](https://github.com/openmls/openmls/pull/1881)
* #1880: [chore(deps): update rstest requirement from 0.24 to 0.26](https://github.com/openmls/openmls/pull/1880)
* #1879: [docs: add docsrs cfg feature and document features](https://github.com/openmls/openmls/pull/1879)
* #1878: [update dependabot](https://github.com/openmls/openmls/pull/1878)
* #1877: [chore(deps): bump actions/checkout from 4 to 5](https://github.com/openmls/openmls/pull/1877)
* #1876: [For `extensions-draft-08` flag, selectively enable optional storage provider dependencies](https://github.com/openmls/openmls/pull/1876)
* #1874: [Add AES-GCM support to libcrux provider, and update libcrux dependencies](https://github.com/openmls/openmls/pull/1874)
* #1872: [feat: add `extensions-draft-08` support to sqlx storage provider](https://github.com/openmls/openmls/pull/1872)
* #1871: [fix: store application export tree after group creation](https://github.com/openmls/openmls/pull/1871)
* #1870: [chore: fix PPRF tests](https://github.com/openmls/openmls/pull/1870)
* #1868: [Implement AppEphemeral proposal and update AppAck implementation](https://github.com/openmls/openmls/pull/1868)

### Contributors
* [@dependabot[bot]](https://github.com/dependabot[bot])
* [@erskingardner](https://github.com/erskingardner)
* [@WaterWhisperer](https://github.com/WaterWhisperer)
* [@kkohbrok](https://github.com/kkohbrok)
* [@wysiwys](https://github.com/wysiwys)
* [@franziskuskiefer](https://github.com/franziskuskiefer)
