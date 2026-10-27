---
type: Styleguide Rule
description: |-
  Use .clone() only when you genuinely need a deep copy. Don't use it as a
  substitute for borrowing; design code to work with the borrow checker. If
  the borrowing relationships become excessively complex, a clone can be a
  pragmatic choice. Cloning Rc/Arc is cheap and expected.
language: rust
category: ownership
rule_id: PREFER-BORROW-OVER-CLONE
priority: warn
tags:
- ownership
- borrowing
- clone
- performance
- google-style
---
Use .clone() only when you genuinely need a deep copy. Don't use it as a
substitute for borrowing; design code to work with the borrow checker. If
the borrowing relationships become excessively complex, a clone can be a
pragmatic choice. Cloning Rc/Arc is cheap and expected.

## Good

- fn total_len(names: &[String]) -> usize {
    names.iter().map(String::len).sum()
}

let n = total_len(&names);
- let shared = Arc::clone(&config); // refcount bump, not a deep copy

## Bad

- fn total_len(names: Vec<String>) -> usize {
    names.iter().map(String::len).sum()
}

let n = total_len(names.clone()); // clone only to satisfy the signature
