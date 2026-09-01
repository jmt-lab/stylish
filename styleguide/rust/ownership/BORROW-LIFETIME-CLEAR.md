---
type: Styleguide Rule
description: |-
  Keep the scope of borrows as small as possible. Release borrows
  before they're no longer needed.
language: rust
category: ownership
rule_id: BORROW-LIFETIME-CLEAR
priority: warn
tags:
- ownership
- lifetimes
- scope
---
Keep the scope of borrows as small as possible. Release borrows
before they're no longer needed.

## Good

- {
    let data = mutex.lock().unwrap();
    process(&data);
} // Lock released
other_work();

## Bad

- let data = mutex.lock().unwrap();
process(&data);
// Long scope, lock held
other_work();
