---
type: Styleguide Rule
description: |-
  Collection transformations should use functional patterns:
  map to transform, filter to select, fold to aggregate.
language: rust
category: functional
rule_id: MAP-FILTER-FOLD
priority: warn
tags:
- functional
- patterns
- carmack
---
Collection transformations should use functional patterns:
map to transform, filter to select, fold to aggregate.

## Good

- let total_damage: f32 = projectiles.iter()
    .filter_map(|p| p.hit_result())
    .map(|hit| hit.damage)
    .sum();

## Bad

- let mut total = 0.0;
for p in &projectiles {
    if let Some(hit) = p.hit_result() {
        total += hit.damage;
    }
}
