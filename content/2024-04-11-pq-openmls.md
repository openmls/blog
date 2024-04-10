---
title: "Post-Quantum OpenMLS"
date: 2024-04-11
tags: ["mls", "pq", "openmls"]
description: "Get started with post-quantum secure end-to-end encrypted with OpenMLS."
notoc: true
author: "Franziskus Kiefer"
author_link: "https://franziskuskiefer.de"
---

OpenMLS now offers security against harvest-now-decrypt-later (HNDL) quantum adversaries.

In [#1546](https://github.com/openmls/openmls/pull/1546) we merged support for the [X-Wing KEM draft](https://www.ietf.org/archive/id/draft-connolly-cfrg-xwing-kem-02.html), which is an early draft for securely combining elliptic-curve-based Diffie-Hellman with ML-KEM. In particular, OpenMLS now supports the ciphersuite MLS_256_XWING_CHACHA20POLY1305_SHA256_Ed25519 with ciphersuite 0x004D. There is no IANA code-point for this ciphersuite yet, such that interoperability may not be guaranteed. We work with other implementers towards interoperability of this ciphersuite.

The implementation uses Cryspen’s [formally verified ML-KEM](https://cryspen.com/post/ml-kem-verification/) and x25519 implementations from [libcrux](https://github.com/cryspen/libcrux/). The implementations are not only formally verified for correctness, secret independence, and memory safety, but also amongst the fastest implementations. Users should not notice any significant performance differences when using this new ciphersuite.
The threat of HNDL attackers requires applications to switch to post-quantum secure mechanisms now, just like [Signal](https://signal.org/blog/pqxdh/) and [iMessage](https://security.apple.com/blog/imessage-pq3/) did already. OpenMLS offers a simple way to achieve security against HNDL attackers and is ready to use.

## Performance

While the new ML-KEM mechanism is very efficient, it requires larger messages and because the ciphersuite used is hybrid, the workload increases.

The following tables give an overview of the performance and message sizes.
One can clearly see an overhead from the post-quantum scheme.
While the computation complexity is not too high, and more efficient implementations of ML-KEM may be used, the communication complexity increases significantly due to the larger key and message sizes in ML-KEM.

##### Computation

|                    | X-Wing + x25519 | x25519    |
| ------------------ | --------------- | --------- |
| Create Key Package | 273.39 µs       | 138.24 µs |
| Create Welcome     | 665.77 µs       | 366.23 µs |
| Join a group       | 733.22 µs       | 313.37 µs |
| Self update        | 650.77 µs       | 294.49 µs |

##### Communication

|                   | X-Wing + x25519 | x25519    |
| ----------------- | --------------- | --------- |
| Key package size  | 2669 Bytes      | 299 Bytes |
| Welcome size      | 5457 Bytes      | 716 Bytes |
| Ratchet tree size | 4007 Bytes      | 408 Bytes |
| Self update size  | 3954 Bytes      | 495 Bytes |

## Next Steps

Using X-Wing as KEM in MLS is the easiest solution to achieve HNDL security for secure group messaging, or any use case that uses the state synchronization protocols specified in MLS.

However, there may be more efficient ways to integrate HNDL protection into MLS by making use of more lightweight KEM combiners because of the way MLS works.
X-Wing is designed as a drop-in KEM scheme with very conservative security guarantees. In the case of MLS a custom KEM scheme may be more efficient.

A new version of OpenMLS will be released later this month, which will include this new, post-quantum secure, ciphersuite.
