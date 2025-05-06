---
title: "This month in OpenMLS #8 - April 2024"
date: 2025-05-06
tags: ["openmls", "this-month-in-openmls"]
notoc: true
author: "Franziskus Kiefer"
---

The openmls project continues to thrive not only because of the core team, but
also thanks to the valuable contributions from our dedicated community.
Last month saw 32 pull requests merged, all aimed at bolstering the stability
and usability of the OpenMLS library.

We added a usable, formally verified crypto backend with [libcrux](https://github.com/cryspen/libcrux)
for use in OpenMLS.
This is the first step towards making OpenMLS a high assurance library.

We also welcome new contributors [@Snazzah](https://github.com/Snazzah), who added
support for external sender proposals [#1750](https://github.com/openmls/openmls/pull/1750),
as well as [@timokoesters](https://github.com/timokoesters).

### Merged PRs April 2025
* #1765: [book: fix link to credentials module](https://github.com/openmls/openmls/pull/1765)
* #1764: [Update rusqlite to 0.32](https://github.com/openmls/openmls/pull/1764)
* #1763: [Fix list of extensions valid in a leaf node](https://github.com/openmls/openmls/pull/1763)
* #1762: [chore: expose LeafNodeSource](https://github.com/openmls/openmls/pull/1762)
* #1760: [Update libcrux provider to use pure Rust crates](https://github.com/openmls/openmls/pull/1760)
* #1759: [doc: Add external add proposal to changelog](https://github.com/openmls/openmls/pull/1759)
* #1758: [chore: Drop stale TODOs](https://github.com/openmls/openmls/pull/1758)
* #1754: [doc: Improve the module documentation](https://github.com/openmls/openmls/pull/1754)
* #1753: [fix: Clippy education](https://github.com/openmls/openmls/pull/1753)
* #1752: [return error when external sender sends commit](https://github.com/openmls/openmls/pull/1752)
* #1750: [Support add proposals from external senders](https://github.com/openmls/openmls/pull/1750)
* #1748: [Add references to validation check valn0113](https://github.com/openmls/openmls/pull/1748)
* #1747: [Remove `binary_tree::test_new_tree_error()` (segfault on 32-bit platforms)](https://github.com/openmls/openmls/pull/1747)
* #1745: [bump wasm threshold to 1.7MiB](https://github.com/openmls/openmls/pull/1745)
* #1744: [Add validation tests for valn0104](https://github.com/openmls/openmls/pull/1744)
* #1739: [Add validation test for valn0108](https://github.com/openmls/openmls/pull/1739)
* #1738: [Path Required: Fix wrong negation in code comment](https://github.com/openmls/openmls/pull/1738)
* #1724: [Add book examples and tests for discarded Commits](https://github.com/openmls/openmls/pull/1724)
* #1721: [Add book example for discarded welcome message](https://github.com/openmls/openmls/pull/1721)

### Contributors
* [@wysiwys](https://github.com/wysiwys)
* [@timokoesters](https://github.com/timokoesters)
* [@raphaelrobert](https://github.com/raphaelrobert)
* [@franziskuskiefer](https://github.com/franziskuskiefer)
* [@Snazzah](https://github.com/Snazzah)
* [@kkohbrok](https://github.com/kkohbrok)
* [@erskingardner](https://github.com/erskingardner)
* [@neekolas](https://github.com/neekolas)
