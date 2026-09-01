---
type: Styleguide Rule
description: |-
  Prefer map, filter, reduce over manual loops. Array methods are
  declarative, composable, and less error-prone.
language: typescript
category: functional
rule_id: ARRAY-METHODS
priority: warn
tags:
- collections
- declarative
- loops
---
Prefer map, filter, reduce over manual loops. Array methods are
declarative, composable, and less error-prone.

## Good

- const active = entities.filter(e => e.isActive);
const ids = active.map(e => e.id);

## Bad

- const active = [];
for (const e of entities) {
  if (e.isActive) active.push(e);
}
