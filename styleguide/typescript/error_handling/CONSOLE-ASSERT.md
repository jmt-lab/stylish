---
type: Styleguide Rule
description: |-
  Assert invariants and preconditions with console.assert. Every function
  should assert its preconditions at the start. These validate programmer
  assumptions, catch contract violations immediately at call site, and
  surface bugs early.
language: typescript
category: error_handling
rule_id: CONSOLE-ASSERT
priority: error
tags:
- assertions
- invariants
- debugging
- preconditions
- contracts
---
Assert invariants and preconditions with console.assert. Every function
should assert its preconditions at the start. These validate programmer
assumptions, catch contract violations immediately at call site, and
surface bugs early.

## Good

- console.assert(entity !== null, 'entity must not be null');
- console.assert(count >= 0 && count <= MAX, 'count out of range');
- console.assert(this.isValid(), 'invalid state');
- function process(entity: Entity): void {
  console.assert(entity !== null);
  console.assert(entity.isValid());
}

## Bad

- // No assertion, assumes entity is valid
entity.update();
- function process(entity: Entity): void {
  // Hope entity is valid
  entity.update();
}
