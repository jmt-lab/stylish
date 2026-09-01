---
type: Styleguide Rule
description: |-
  When breaking out of nested loops, use loop labels to
  make intent clear.
language: rust
category: control_flow
rule_id: LOOP-LABELS
priority: info
tags:
- control-flow
- loops
- clarity
---
When breaking out of nested loops, use loop labels to
make intent clear.

## Good

- 'outer: for x in 0..10 {
    for y in 0..10 {
        if found { break 'outer; }
    }
}

## Bad

- let mut done = false;
for x in 0..10 {
    for y in 0..10 {
        if found { done = true; break; }
    }
    if done { break; }
}
