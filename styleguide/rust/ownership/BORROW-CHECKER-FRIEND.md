---
type: Styleguide Rule
description: |-
  If fighting the borrow checker, restructure code rather than using
  unsafe or complex patterns. The checker catches real bugs.
language: rust
category: ownership
rule_id: BORROW-CHECKER-FRIEND
priority: error
tags:
- ownership
- safety
- philosophy
- carmack
---
If fighting the borrow checker, restructure code rather than using
unsafe or complex patterns. The checker catches real bugs.

## Good

- // Split borrows cleanly
let (first, rest) = slice.split_first_mut().unwrap();

## Bad

- // Don't use unsafe to bypass borrow checker without justification
unsafe { &mut *ptr } // Why?
