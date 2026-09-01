---
type: Styleguide Rule
description: |-
  Structure tests with three sections: Arrange (setup), Act (execute),
  Assert (verify). Use blank lines to separate sections. For trivially
  simple pure functions, a one-liner assertion is acceptable.
language: rust
category: testing
rule_id: AAA-PATTERN
priority: warn
tags:
- testing
- structure
- readability
---
Structure tests with three sections: Arrange (setup), Act (execute),
Assert (verify). Use blank lines to separate sections. For trivially
simple pure functions, a one-liner assertion is acceptable.

## Good

- #[test]
fn test_add() {
    let a = 5;
    let b = 3;

    let result = add(a, b);

    assert_eq!(result, 8);
}


## Bad

- #[test]
fn test_add() {
    assert_eq!(add(5, 3), 8);
}

