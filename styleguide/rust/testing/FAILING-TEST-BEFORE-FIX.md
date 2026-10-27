---
type: Styleguide Rule
description: |-
  Before fixing a bug, write a test that reproduces it and fails; then fix
  the code. Before refactoring untested code, pin its current behavior with
  characterization tests.
language: rust
category: testing
rule_id: FAILING-TEST-BEFORE-FIX
priority: info
tags:
- testing
- bugs
- regression
- beautiful-rust
---
Before fixing a bug, write a test that reproduces it and fails; then fix
the code. Before refactoring untested code, pin its current behavior with
characterization tests.

## Good

- #[test]
fn test_parse_duration_trailing_whitespace_regression() {
    assert_eq!(parse_duration("5s ")?, Duration::from_secs(5)); // failed before the fix
}

## Bad

- // fix committed with no test; the bug returns in the next refactor
