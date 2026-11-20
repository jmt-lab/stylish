---
type: Styleguide Rule
description: |-
  In hot maps whose keys never come from untrusted input, consider a
  faster non-DoS-resistant hasher such as rustc_hash::FxHashMap or ahash,
  after profiling shows hashing matters. Keep the default SipHash for
  anything keyed by external data.
language: rust
category: optimization
rule_id: FAST-HASHER-FOR-TRUSTED-KEYS
priority: info
tags:
- optimization
- collections
- hashing
- security
- rust-skills
---
In hot maps whose keys never come from untrusted input, consider a
faster non-DoS-resistant hasher such as rustc_hash::FxHashMap or ahash,
after profiling shows hashing matters. Keep the default SipHash for
anything keyed by external data.

## Good

- // Keys are interned compiler symbols; profiling showed 18% of time in SipHash.
let mut types: FxHashMap<SymbolId, TypeInfo> = FxHashMap::default();

## Bad

- // HTTP header names from clients: attacker-chosen keys can trigger collision floods.
let mut headers: FxHashMap<String, String> = FxHashMap::default();
