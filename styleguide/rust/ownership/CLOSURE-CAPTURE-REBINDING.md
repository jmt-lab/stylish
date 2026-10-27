---
type: Styleguide Rule
description: |-
  When a move closure needs some values cloned or borrowed and others
  moved, rebind them in a block just before the closure instead of cloning
  everything up front or juggling names.
language: rust
category: ownership
rule_id: CLOSURE-CAPTURE-REBINDING
priority: info
tags:
- ownership
- closures
- move
- beautiful-rust
---
When a move closure needs some values cloned or borrowed and others
moved, rebind them in a block just before the closure instead of cloning
everything up front or juggling names.

## Good

- let job = {
    let config = Arc::clone(&config);
    let name = name.as_str();
    move || run(config, name, data)
};

## Bad

- let config2 = config.clone();
let name2 = name.clone();
let data2 = data;
let job = move || run(config2, &name2, data2);
