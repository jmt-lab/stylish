---
type: Styleguide Rule
description: |-
  Don't hand-write trait implementations that #[derive()] can produce with
  the same behavior. Write a manual impl only when the behavior must differ
  (e.g. ignoring a field, redacting secrets in Debug).
language: rust
category: traits
rule_id: PREFER-DERIVE
priority: warn
tags:
- traits
- derive
- boilerplate
- google-style
---
Don't hand-write trait implementations that #[derive()] can produce with
the same behavior. Write a manual impl only when the behavior must differ
(e.g. ignoring a field, redacting secrets in Debug).

## Good

- #[derive(Clone, Debug, PartialEq, Eq)]
pub struct Point { x: i32, y: i32 }

## Bad

- impl PartialEq for Point {
    fn eq(&self, other: &Self) -> bool {
        self.x == other.x && self.y == other.y
    }
}
