---
title: "This month in OpenMLS #18 - February 2026"
date: 2026-03-04
tags: ["openmls", "this-month-in-openmls"]
notoc: true
author: "Franziskus Kiefer"
---


In February, we merged 17 pull requests.

The TreeSync module now has public accessors to make it easier for developers to
inspect, the state of the Ratchet Tree.
This may be used to optimize commit behaviour.

We also released new point releases for OpenMLS, picking up security fixes in
dependencies.
We recommend everyone to update.

### v0.8.1

#### New features
- [#1955](https://github.com/openmls/openmls/pull/1955): Expose functions that allow access to (blank) leaves and parent nodes

#### Changed

- [#1964](https://github.com/openmls/openmls/pull/1964): update libcrux and rust_crypto provider dependencies, due to https://github.com/cryspen/libcrux/security/advisories/GHSA-435g-fcv3-8j26 and https://github.com/cryspen/hpke-rs/security/advisories/GHSA-g433-pq76-6cmf

#### Links

* [Github Release](https://github.com/openmls/openmls/releases/tag/openmls-v0.8.1)
* [Crate](https://crates.io/crates/openmls/0.8.1)
    
### v0.7.4

The security fixes for libcrux and rust_crypto provider dependencies were backported to the v0.7 release as v0.7.4.

#### Links

* [Github Release](https://github.com/openmls/openmls/releases/tag/openmls-v0.7.4)
* [Crate](https://crates.io/crates/openmls/0.7.4)
    
### Other releases
    
Also released in February were OpenMLS [v0.8.0](https://github.com/openmls/blog/blob/main/content/posts/2026-02-05-this-month-in-openmls.md#v080),
v0.7.3 and
[v0.7.2](https://github.com/openmls/blog/blob/main/content/posts/2026-02-05-this-month-in-openmls.md#v072) (also see [This Month in OpenMLS #17](https://blog.openmls.tech/posts/2026-02-05-this-month-in-openmls/))


## Merged PRs February 2026
* \#1965: [Derive TlsSerializeBytes for SignatureScheme](https://github.com/openmls/openmls/pull/1965)
* \#1964: [chore: prepare 0.8.1 release](https://github.com/openmls/openmls/pull/1964)
* \#1962: [update libcrux and hpke-rs depdencenies](https://github.com/openmls/openmls/pull/1962)
* \#1959: [Expose TreeSync for MlsGroup and PublicGroup](https://github.com/openmls/openmls/pull/1959)
* \#1955: [TreeSync: expose full_leaves/parents; make full_leaves provide LeafNodeIndex](https://github.com/openmls/openmls/pull/1955)
* \#1954: [update ciphersuites in book](https://github.com/openmls/openmls/pull/1954)
* \#1953: [chore: bump memory provider version to 0.5.0](https://github.com/openmls/openmls/pull/1953)
* \#1952: [chore: prep v0.8.0 release](https://github.com/openmls/openmls/pull/1952)
* \#1950: [feat: derive serde Serialize and Deserialize for MlsMessageOut](https://github.com/openmls/openmls/pull/1950)
* \#1949: [Relax Wasm size limit](https://github.com/openmls/openmls/pull/1949)
* \#1948: [update changelog](https://github.com/openmls/openmls/pull/1948)
* \#1945: [update libcrux and hpke deps](https://github.com/openmls/openmls/pull/1945)
* \#1944: [fix: correctly access credentials from past epochs](https://github.com/openmls/openmls/pull/1944)
* \#1943: [fix: skip removed members in capabilities check](https://github.com/openmls/openmls/pull/1943)
* \#1936: [Add APIs to access information about the next epoch from a StagedCommit](https://github.com/openmls/openmls/pull/1936)
* \#1933: [Add and document more validation checks](https://github.com/openmls/openmls/pull/1933)
* \#1929: [feat: don't replace groups by default](https://github.com/openmls/openmls/pull/1929)

### Contributors
* [@franziskuskiefer](https://github.com/franziskuskiefer)
* [@keks](https://github.com/keks)
* [@kkohbrok](https://github.com/kkohbrok)
