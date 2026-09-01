---
type: Styleguide Rule
description: |-
  For union types, use switch with default case that assigns to never.
  The compiler will error if a case is missed, ensuring all cases are
  handled at compile time. This makes state transitions explicit and
  prevents silent bugs when new union members are added.
language: typescript
category: control_flow
rule_id: TS-EXHAUSTIVE-SWITCH
priority: error
tags:
- switch
- exhaustiveness
- type-safety
- unions
- correctness
---
For union types, use switch with default case that assigns to never.
The compiler will error if a case is missed, ensuring all cases are
handled at compile time. This makes state transitions explicit and
prevents silent bugs when new union members are added.

## Good

- switch (type) {
  case 'a': return handleA();
  case 'b': return handleB();
  default: {
    const _: never = type;
    throw new Error(`Unhandled: ${type}`);
  }
}
- default: const _exhaustive: never = value; throw new Error(`Unhandled: ${value}`);

## Bad

- switch (type) {
  case 'a': return handleA();
  case 'b': return handleB();
  // Missing default
}
- default: throw new Error('Unknown'); // No compile-time check
