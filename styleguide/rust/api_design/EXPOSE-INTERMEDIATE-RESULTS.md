---
type: Styleguide Rule
description: |-
  Return useful work you've already done instead of discarding it:
  binary_search returns the insertion point on a miss, HashMap::insert returns
  the previous value, and from_utf8's error reports the valid prefix.
language: rust
category: api_design
rule_id: EXPOSE-INTERMEDIATE-RESULTS
priority: info
tags:
- api-design
- flexibility
- beautiful-rust
---
Return useful work you've already done instead of discarding it:
binary_search returns the insertion point on a miss, HashMap::insert returns
the previous value, and from_utf8's error reports the valid prefix.

## Good

- pub fn insert(&mut self, key: Key, value: Value) -> Option<Value> { ... } // returns old value

## Bad

- pub fn insert(&mut self, key: Key, value: Value) -> bool { ... } // old value dropped
