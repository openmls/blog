---
title: "This month in OpenMLS #13 - September 2025"
date: 2025-10-01
tags: ["openmls", "this-month-in-openmls"]
notoc: true
author: "Franziskus Kiefer"
---

We merged 15 PRs in September and released OpenMLSv0.7.1.

### v0.7.1 Release 🔐
The most critical update this month was the release of v0.7.1, which addresses
a security vulnerability.
We urge all users to upgrade to this version as soon as possible to ensure their
applications remains secure.
You can find more details about the vulnerability in the official security
advisory: [GHSA-qr9h-x63w-vqfm](https://github.com/openmls/openmls/security/advisories/GHSA-qr9h-x63w-vqfm).

### New Features and Fixes 🚀
September and this release also saw the addition of some handy new features and
important bug fixes:

* Check for Pending Proposals: A new function has been added to easily check if there are any pending proposals in a group ([#1840](https://github.com/openmls/openmls/pull/1840)).
* External Commit Builder Fix: A regression in the external commit builder has been addressed ([#1842](https://github.com/openmls/openmls/pull/1842)).
* Forward secure exporter: We added "Safe exporters" as defined in the [MLS extension draft](https://messaginglayersecurity.rocks/mls-extensions/draft-ietf-mls-extensions.html) behind the `extensions-draft-08` feature flag. Previously serialized groups will derive the exporter upon creating/processing and merging the next commit. ([#1725](https://github.com/openmls/openmls/pull/1725)).
* New External Commit Builder: A new builder pattern for external commits has been introduced with `MlsGroup::external_commit_builder` ([#1801](https://github.com/openmls/openmls/pull/1801)). Consequently, the old `MlsGroup::join_by_external_commit` method is now deprecated. We also fixed a regression related to this new builder in #1842.
* Check for Pending Proposals: You can now easily see if a group has unprocessed proposals using the new `MlsGroup::has_pending_proposals()` method ([#1840](https://github.com/openmls/openmls/pull/1840)).
* Flexible Lifetime Validation: For advanced use cases, it's now possible to disable leaf node lifetime validation when joining a group via `StagedWelcome::build_from_welcome` ([#1814](https://github.com/openmls/openmls/pull/1814)).

### Contributors 🎉

We are also thrilled to welcome [@nuke-web3](https://github.com/nuke-web3) as a
new contributor.

### Merged PRs September 2025
* #1853: [chore: release v0.7.1](https://github.com/openmls/openmls/pull/1853)
* #1852: [chore: follow up on v0.7.1](https://github.com/openmls/openmls/pull/1852)
* #1851: [chore: No external pub extension in welcome group info](https://github.com/openmls/openmls/pull/1851)
* #1850: [chore: prepare v0.7.1 release](https://github.com/openmls/openmls/pull/1850)
* #1849: [perf: Avoid storing the whole group state after decryption](https://github.com/openmls/openmls/pull/1849)
* #1848: [test: separate providers](https://github.com/openmls/openmls/pull/1848)
* #1847: [test: new persistence tests covering more group operations](https://github.com/openmls/openmls/pull/1847)
* #1846: [fix: Persistence during message processing](https://github.com/openmls/openmls/pull/1846)
* #1845: [chore: rustc 1.90 clippy fixes](https://github.com/openmls/openmls/pull/1845)
* #1842: [fix: external commit builder regression](https://github.com/openmls/openmls/pull/1842)
* #1841: [chore: clippy fixes in fork resolution feature](https://github.com/openmls/openmls/pull/1841)
* #1840: [feat: Add function to check if there are pending proposals](https://github.com/openmls/openmls/pull/1840)
* #1838: [box large enum variants](https://github.com/openmls/openmls/pull/1838)
* #1832: [Improve Lifetime log message](https://github.com/openmls/openmls/pull/1832)
* #1817: [Book corrections and fixes, prettier fmt *.md files](https://github.com/openmls/openmls/pull/1817)
* #1725: [Add fs exporter](https://github.com/openmls/openmls/pull/1725)

### Contributors
* [@nuke-web3](https://github.com/nuke-web3)
* [@kkohbrok](https://github.com/kkohbrok)
* [@wysiwys](https://github.com/wysiwys)
* [@franziskuskiefer](https://github.com/franziskuskiefer)
* [@raphaelrobert](https://github.com/raphaelrobert)
* [@timokoesters](https://github.com/timokoesters)
