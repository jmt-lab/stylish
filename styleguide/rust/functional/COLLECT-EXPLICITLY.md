---
type: Styleguide Rule
description: |-
  Make it clear when you're materializing an iterator into a
  collection with .collect().
language: rust
category: functional
rule_id: COLLECT-EXPLICITLY
priority: info
tags:
- functional
- iterators
- clarity
---
Make it clear when you're materializing an iterator into a
collection with .collect().

## Good

- let results: Vec<_> = items.iter()
    .map(|x| x * 2)
    .collect();

## Bad

- let results = items.iter().map(|x| x * 2); // Returns iterator, not collection
