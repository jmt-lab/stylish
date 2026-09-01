---
type: Styleguide Rule
description: |-
  Mark panic tests with #[should_panic]. Add expected parameter
  to verify panic message. Prefer Result-based errors when possible.
language: rust
category: testing
rule_id: SHOULD-PANIC-USAGE
priority: warn
tags:
- testing
- panics
- verification
---
Mark panic tests with #[should_panic]. Add expected parameter
to verify panic message. Prefer Result-based errors when possible.

## Good

- #[test]
#[should_panic(expected = "index out of bounds")]
fn test_invalid_index_panics() {
    let v = vec![1, 2];
    v[10];
}


## Bad

- #[test]
#[should_panic]
fn test_panics() {  // No expected message
    panic!("oops");
}

