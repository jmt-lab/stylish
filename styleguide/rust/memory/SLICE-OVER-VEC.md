---
type: Styleguide Rule
description: |-
  Functions that only read a collection should accept &[T], not &Vec<T>.
  This is more flexible and communicates intent.
language: rust
category: memory
rule_id: SLICE-OVER-VEC
priority: warn
tags:
- memory
- api-design
- flexibility
---
Functions that only read a collection should accept &[T], not &Vec<T>.
This is more flexible and communicates intent.

## Good

- fn process_entities(entities: &[Entity])

## Bad

- fn process_entities(entities: &Vec<Entity>) // Too specific
