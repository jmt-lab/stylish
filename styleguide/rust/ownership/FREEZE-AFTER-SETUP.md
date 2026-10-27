---
type: Styleguide Rule
description: |-
  When a value needs mutation only during setup, rebind it immutably
  afterward (let data = data;) or build it in a block, so later code can't
  change it by accident.
language: rust
category: ownership
rule_id: FREEZE-AFTER-SETUP
priority: info
tags:
- ownership
- mutability
- immutability
- beautiful-rust
---
When a value needs mutation only during setup, rebind it immutably
afterward (let data = data;) or build it in a block, so later code can't
change it by accident.

## Good

- let mut ids = load_ids()?;
ids.sort_unstable();
ids.dedup();
let ids = ids;
- let ids = {
    let mut ids = load_ids()?;
    ids.sort_unstable();
    ids
};

## Bad

- let mut ids = load_ids()?;
ids.sort_unstable();
// 200 lines later, ids is still mutable
ids.push(extra_id);
