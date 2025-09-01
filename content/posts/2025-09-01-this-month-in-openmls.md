---
title: "This month in OpenMLS #12 - August 2025"
date: 2025-09-01
tags: ["openmls", "this-month-in-openmls"]
notoc: true
author: "Franziskus Kiefer"
---

We merged 8 PRs in August. Not bad for a summer month 🌞.

We welcome [@tbehner](https://github.com/tbehner) as a first time contributor, solving
a long standing issue by [adding the hmac function to OpenMlsCrypto](https://github.com/openmls/openmls/pull/1825) trait.

Thanks to [@kkohbrok](https://github.com/kkohbrok) it is now also much easier to
build external commits with the new [external commit builder](https://github.com/openmls/openmls/pull/1801).

```Rust
let (mut dave_group, _bundle) = MlsGroup::external_commit_builder()
    .with_config(mls_group_config.clone())
    .build_group(provider, verifiable_group_info, dave_credential)
    .unwrap()
    .load_psks(provider.storage())
    .unwrap()
    .build(
        provider.rand(),
        provider.crypto(),
        &dave_signature_keys,
        |_| true,
    )
    .unwrap()
    .finalize(provider)
    .expect("Error joining from external commit");
```

### Merged PRs August 2025
* #1829: [Doc fixes](https://github.com/openmls/openmls/pull/1829)
* #1828: [disable large tree test](https://github.com/openmls/openmls/pull/1828)
* #1825: [adding the hmac function to OpenMlsCrypto](https://github.com/openmls/openmls/pull/1825)
* #1824: [make clippy happy](https://github.com/openmls/openmls/pull/1824)
* #1823: [Update README.md in sqlite storage](https://github.com/openmls/openmls/pull/1823)
* #1822: [chore: Add TryFrom for VerifiableCiphersuite](https://github.com/openmls/openmls/pull/1822)
* #1814: [Allow configuration of leaf node lifetime checks on join](https://github.com/openmls/openmls/pull/1814)
* #1801: [External commit builder](https://github.com/openmls/openmls/pull/1801)

### Contributors
* [@wysiwys](https://github.com/wysiwys)
* [@franziskuskiefer](https://github.com/franziskuskiefer)
* [@tbehner](https://github.com/tbehner)
* [@kkohbrok](https://github.com/kkohbrok)
