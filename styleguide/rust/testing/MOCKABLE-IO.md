---
type: Styleguide Rule
description: |-
  Types that touch the file system, network, clock, or randomness must be
  testable without them: inject the dependency (trait, closure, or impl Read)
  or provide a test constructor (e.g. new_mocked() -> (Self, MockCtrl) behind
  test-util). Don't offer a Default that performs I/O.
language: rust
category: testing
rule_id: MOCKABLE-IO
priority: warn
tags:
- testing
- mocks
- io
- determinism
- beautiful-rust
---
Types that touch the file system, network, clock, or randomness must be
testable without them: inject the dependency (trait, closure, or impl Read)
or provide a test constructor (e.g. new_mocked() -> (Self, MockCtrl) behind
test-util). Don't offer a Default that performs I/O.

## Good

- pub struct TokenCache<C: Clock = SystemClock> { clock: C, ... }

#[cfg(feature = "test-util")]
impl TokenCache<MockClock> { pub fn new_mocked() -> (Self, MockClock) { ... } }

## Bad

- impl Default for TokenCache {
    fn default() -> Self { Self { now: SystemTime::now(), file: File::open(PATH).unwrap() } }
}
