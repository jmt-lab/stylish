---
type: Styleguide Rule
description: |-
  Use /// for what users of an item need to know and // for implementation
  notes, TODOs, and commented-out code. Mixing both on the same item is
  encouraged when each audience has something to learn.
language: rust
category: documentation
rule_id: MIX-DOC-AND-IMPL-COMMENTS
priority: info
tags:
- documentation
- comments
- google-style
---
Use /// for what users of an item need to know and // for implementation
notes, TODOs, and commented-out code. Mixing both on the same item is
encouraged when each audience has something to learn.

## Good

- /// Finds the first `Item` with the given `name`, or `None` if not present.
// TODO(#1234): take `name` as &str instead of String.
pub fn find_named(items: &[Item], name: String) -> Option<&Item> { ... }

## Bad

- /// Finds the first `Item` with the given `name`, or `None` if not present.
/// TODO(#1234): take `name` as &str instead of String.
pub fn find_named(items: &[Item], name: String) -> Option<&Item> { ... }
