---
type: Styleguide Rule
description: |-
  When consuming an iterator that returns Option, while let
  is clearer than loop + match.
language: rust
category: control_flow
rule_id: WHILE-LET-ITERATION
priority: info
tags:
- control-flow
- iterators
- idiom
---
When consuming an iterator that returns Option, while let
is clearer than loop + match.

## Good

- while let Some(item) = iter.next() {
    process(item);
}

## Bad

- loop {
    match iter.next() {
        Some(item) => process(item),
        None => break,
    }
}
