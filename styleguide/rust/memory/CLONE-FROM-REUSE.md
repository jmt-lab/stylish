---
type: Styleguide Rule
description: |-
  When you repeatedly overwrite an existing value with a clone, use
  target.clone_from(&source) instead of target = source.clone(), so
  String, Vec, and other collections can reuse their allocation.
language: rust
category: memory
rule_id: CLONE-FROM-REUSE
priority: info
tags:
- memory
- allocation
- clone
- rust-skills
---
When you repeatedly overwrite an existing value with a clone, use
target.clone_from(&source) instead of target = source.clone(), so
String, Vec, and other collections can reuse their allocation.

## Good

- for frame in frames {
    previous.clone_from(&current);
    current.decode_into(frame);
}

## Bad

- for frame in frames {
    previous = current.clone(); // frees and reallocates every iteration
    current.decode_into(frame);
}
