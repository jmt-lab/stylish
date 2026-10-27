---
type: Styleguide Rule
description: |-
  Don't write tests that restate constants or mirror implementation
  branches. Test observable behavior and properties: round-trips,
  monotonicity, idempotence, invariants.
language: rust
category: testing
rule_id: NO-TAUTOLOGICAL-TESTS
priority: warn
tags:
- testing
- quality
- beautiful-rust
---
Don't write tests that restate constants or mirror implementation
branches. Test observable behavior and properties: round-trips,
monotonicity, idempotence, invariants.

## Good

- #[test]
fn test_checkpoints_evenly_spaced() {
    let gaps: Vec<_> = CHECKPOINTS.windows(2).map(|w| w[1] - w[0]).collect();
    assert!(gaps.iter().all(|&g| g == gaps[0]), "uneven gaps: {gaps:?}");
}
- #[test]
fn test_encode_decode_round_trip() {
    assert_eq!(decode(&encode(&msg))?, msg);
}

## Bad

- #[test]
fn test_checkpoints() {
    assert_eq!(CHECKPOINTS, [0, 90, 180, 270]);
}
