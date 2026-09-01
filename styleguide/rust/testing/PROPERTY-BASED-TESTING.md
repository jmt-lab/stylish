---
type: Styleguide Rule
description: |-
  Use proptest or quickcheck to test invariants with random inputs.
  Good for parsers, encoders, and mathematical functions.
language: rust
category: testing
rule_id: PROPERTY-BASED-TESTING
priority: info
tags:
- testing
- property-based
- coverage
---
Use proptest or quickcheck to test invariants with random inputs.
Good for parsers, encoders, and mathematical functions.

## Good

- proptest! {
    #[test]
    fn test_encode_decode_roundtrip(data: Vec<u8>) {
        assert_eq!(decode(encode(&data)), data);
    }
}


## Bad

- // Only test with hardcoded examples
