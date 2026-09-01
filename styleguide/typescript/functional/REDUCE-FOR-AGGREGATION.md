---
type: Styleguide Rule
description: |-
  When aggregating collections, use reduce instead of loops with
  accumulators. Reduce is declarative and composable.
language: typescript
category: functional
rule_id: REDUCE-FOR-AGGREGATION
priority: info
tags:
- reduce
- aggregation
- declarative
---
When aggregating collections, use reduce instead of loops with
accumulators. Reduce is declarative and composable.

## Good

- const total = items.reduce((sum, item) => sum + item.value, 0);
- const grouped = items.reduce((acc, item) => ({...acc, [item.id]: item}), {});

## Bad

- let total = 0;
for (const item of items) {
  total += item.value;
}
