---
title: "This month in OpenMLS #14 - October 2025"
date: 2025-11-01
tags: ["openmls", "this-month-in-openmls"]
notoc: true
author: "Franziskus Kiefer"
---

We merged 10 PRs in October.

### New Features and Fixes 🚀
This month saw a number of improvements and additions.

* **New `sqlx` based storage provider**: A new storage provider based on `sqlx` has been added, offering a another robust and feature-rich alternative for persistence ([1854](https://github.com/openmls/openmls/pull/1854)).
* **Performance improvements**: We've added a new `from_components` method to `TreeNode` to avoid unnecessary allocations, which should give a nice performance boost in tree operations ([1864](https://github.com/openmls/openmls/pull/1864)).
* **PSK Validation**: Pre-shared key validation has been improved, especially when processing Welcome messages ([1862](https://github.com/openmls/openmls/pull/1862), [1863](https://github.com/openmls/openmls/pull/1863)).
* **API Re-addition**: Make it easier to re-add clients that got forked ([1855](https://github.com/openmls/openmls/pull/1855)).
* **Validation Fixes**: We continue to improve our validation logic. This month we updated the validation for extension types in leaf node extensions ([1831](https://github.com/openmls/openmls/pull/1831)) and fixed references to the validation dashboard in some of our tests ([1861](https://github.com/openmls/openmls/pull/1861)).

### Contributors 🎉
We are also thrilled to welcome [@WaterWhisperer](https://github.com/WaterWhisperer) as a
new contributor.


### Merged PRs October 2025
* #1865: [doc: correct RFC section reference in key schedule documentation](https://github.com/openmls/openmls/pull/1865)
* #1864: [feat: add from_components method to avoid allocations in TreeNode](https://github.com/openmls/openmls/pull/1864)
* #1863: [chore: update PSK validation id comments](https://github.com/openmls/openmls/pull/1863)
* #1862: [chore: psk validation when processing welcome messages](https://github.com/openmls/openmls/pull/1862)
* #1861: [Fix references to validation dashboard for some tests](https://github.com/openmls/openmls/pull/1861)
* #1858: [chore: allow deprecated warnings in rustcrypto for now](https://github.com/openmls/openmls/pull/1858)
* #1857: [chore: extend changelog from #1855](https://github.com/openmls/openmls/pull/1857)
* #1855: [re-add api](https://github.com/openmls/openmls/pull/1855)
* #1854: [feat: add sqlx based storage provider](https://github.com/openmls/openmls/pull/1854)
* #1831: [Update validation for extension types of leaf node extensions](https://github.com/openmls/openmls/pull/1831)

### Contributors
* [@wysiwys](https://github.com/wysiwys)
* [@raphaelrobert](https://github.com/raphaelrobert)
* [@franziskuskiefer](https://github.com/franziskuskiefer)
* [@WaterWhisperer](https://github.com/WaterWhisperer)
* [@kkohbrok](https://github.com/kkohbrok)
* [@keks](https://github.com/keks)
