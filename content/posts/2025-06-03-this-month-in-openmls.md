---
title: "This month in OpenMLS #9 - May 2025"
date: 2025-06-03
tags: ["openmls", "this-month-in-openmls"]
notoc: true
author: "Franziskus Kiefer"
---

We merged 4 PRs in May with some significant improvements.

[#1774](https://github.com/openmls/openmls/pull/1774) introduced a flag in the
commit builder, providing more granular control over group information creation.
This enhancement allows for greater flexibility when managing MLS group states.

We've improved error handling for old private messages in [#1772](https://github.com/openmls/openmls/pull/1772).
Now, when you encounter an outdated private message, OpenMLS will return a more
specific error, making debugging and message management easier.

And [#1767](https://github.com/openmls/openmls/pull/1767) refines how updates are
handled within OpenMLS by transitioning to the use of SignerBundle instead of
Signer.

### Merged PRs May 2025
* #1774: [feat: group info creation flag in commit builder](https://github.com/openmls/openmls/pull/1774)
* #1772: [chore: suppress `result_large_err` lint in interop client](https://github.com/openmls/openmls/pull/1772)
* #1767: [fix: Return a more specific error message for old private messages](https://github.com/openmls/openmls/pull/1767)
* #1766: [Use SignerBundle instead of Signer for update](https://github.com/openmls/openmls/pull/1766)

### Contributors
* [@raphaelrobert](https://github.com/raphaelrobert)
* [@kkohbrok](https://github.com/kkohbrok)
