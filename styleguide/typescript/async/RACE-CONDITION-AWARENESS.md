---
type: Styleguide Rule
description: |-
  Async code creates race conditions. Document assumptions about execution
  order and state validity across await points.
language: typescript
category: async
rule_id: RACE-CONDITION-AWARENESS
priority: warn
tags:
- concurrency
- state
- documentation
---
Async code creates race conditions. Document assumptions about execution
order and state validity across await points.

## Good

- // Assumes this.state unchanged across await
const data = await fetch();
assert(this.state === expectedState);

## Bad

- const data = await fetch();
this.state.update(data); // State may have changed during await
