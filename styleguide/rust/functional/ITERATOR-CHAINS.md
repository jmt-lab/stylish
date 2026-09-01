---
type: Styleguide Rule
description: |-
  Iterator combinators (map, filter, fold) are more declarative,
  composable, and often optimize better than manual loops.
language: rust
category: functional
rule_id: ITERATOR-CHAINS
priority: warn
tags:
- functional
- iterators
- carmack
---
Iterator combinators (map, filter, fold) are more declarative,
composable, and often optimize better than manual loops.

## Good

- let alive: Vec<_> = entities.iter()
    .filter(|e| e.is_alive())
    .filter(|e| e.in_range(player))
    .take(MAX_TRACKED)
    .collect();

## Bad

- let mut alive = Vec::new();
for e in &entities {
    if e.is_alive() && e.in_range(player) {
        if alive.len() < MAX_TRACKED {
            alive.push(e);
        }
    }
}
