---
title: "This month in OpenMLS #3 - November 2024"
date: 2024-12-03
tags: ["openmls", "this-month-in-openmls"]
notoc: true
author: "Franziskus Kiefer"
---

In November we merged 9 PRs into OpenMLS.

A major change has been the addition of a commit builder in [#1675](https://github.com/openmls/openmls/pull/1675).
The commit builder makes creating commits more convenient as you can see in the example below.

```rust
let message_bundle = alice_group
    .commit_builder()
    .propose_adds(Some(bob_key_package.key_package().clone()))
    .load_psks(provider.storage())
    .expect("error loading psks")
    .build(
        provider.rand(),
        provider.crypto(),
        &alice_signature_keys,
        |_proposal| true,
    )
    .expect("error validating data and building commit")
    .stage_commit(provider)
    .expect("error staging commit");

let (mls_message_out, welcome, group_info) = message_bundle.into_contents();
```


### Merged PRs November 2024
* #1687: [Clippy fixes](https://github.com/openmls/openmls/pull/1687)
* #1684: [Add validation annotations and a check](https://github.com/openmls/openmls/pull/1684)
* #1683: [ci: Fix coverage](https://github.com/openmls/openmls/pull/1683)
* #1679: [Fixing a few typos in the book](https://github.com/openmls/openmls/pull/1679)
* #1678: [Update README.md ciphersuite names](https://github.com/openmls/openmls/pull/1678)
* #1676: [Fix docs link](https://github.com/openmls/openmls/pull/1676)
* #1675: [Add Commit Builder](https://github.com/openmls/openmls/pull/1675)
* #1673: [Feat: Better error when attempting to decrypt own messages](https://github.com/openmls/openmls/pull/1673)
* #1672: [`VerifiableGroupInfo::epoch()` added to public API](https://github.com/openmls/openmls/pull/1672)

### Contributors
* [@franziskuskiefer](https://github.com/franziskuskiefer)
* [@kkohbrok](https://github.com/kkohbrok)
* [@raphaelrobert](https://github.com/raphaelrobert)
* [@josephlukefahr](https://github.com/josephlukefahr)
* [@keks](https://github.com/keks)
