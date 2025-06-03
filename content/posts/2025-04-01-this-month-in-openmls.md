---
title: "This month in OpenMLS #7 - March 2025"
date: 2025-04-01
tags: ["openmls", "this-month-in-openmls"]
notoc: true
author: "Franziskus Kiefer"
---

OpenMLS saw some significant improvements last month!
We tackled several bugs and introduced two key features:
a helper to streamline fork resolution ([#1731](https://github.com/openmls/openmls/pull/1731)) and the much-requested ability to
rotate signature keys ([#1735](https://github.com/openmls/openmls/pull/1735)).
Additionally, a big thank you to [@wysiwys](https://github.com/wysiwys) for
contributing a new set of helpers that will make writing tests significantly easier.

We're particularly excited about the fork resolution helper, and we'll be diving
deeper into the intricacies of this issue and its solution in a dedicated blog
post coming soon.

### Merged PRs March 2025
* #1735: [add ability to rotate signature keys](https://github.com/openmls/openmls/pull/1735)
* #1731: [Add Helpers for resolving forks](https://github.com/openmls/openmls/pull/1731)
* #1730: [Single group test framework](https://github.com/openmls/openmls/pull/1730)
* #1728: [Disable `test_new_tree_error()` due to segfault](https://github.com/openmls/openmls/pull/1728)
* #1726: [Don't store `PublicGroup` in storage in `PublicGroup::from_external()`](https://github.com/openmls/openmls/pull/1726)
* #1709: [feat(wasm): add binding for MlsGroup.create_message()](https://github.com/openmls/openmls/pull/1709)

### Contributors
* [@franziskuskiefer](https://github.com/franziskuskiefer)
* [@wysiwys](https://github.com/wysiwys)
* [@sandr01d](https://github.com/sandr01d)
* [@keks](https://github.com/keks)
* [@kkohbrok](https://github.com/kkohbrok)
