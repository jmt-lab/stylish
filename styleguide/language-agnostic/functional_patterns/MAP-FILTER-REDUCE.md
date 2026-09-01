---
type: Styleguide Rule
description: |-
  Use functional patterns (map, filter, reduce) for simple, stateless
  collection transforms. For complex logic with side effects, prefer
  explicit loops (see EXPLICIT-LOOPS in control_flow.yaml).
language: language-agnostic
category: functional_patterns
rule_id: MAP-FILTER-REDUCE
priority: info
tags:
- collections
- patterns
- declarative
---
Use functional patterns (map, filter, reduce) for simple, stateless
collection transforms. For complex logic with side effects, prefer
explicit loops (see EXPLICIT-LOOPS in control_flow.yaml).

## Good

- active = Filter(entities, IsActive);
positions = Map(active, GetPosition);
total = Reduce(positions, Sum);

## Bad

- // Using map/filter for complex logic with side effects
Map(entities, [&](e) { log(e); db.update(e); return transform(e); });
