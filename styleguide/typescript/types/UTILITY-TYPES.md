---
type: Styleguide Rule
description: |-
  Leverage Partial, Required, Readonly, Pick, Omit, etc. instead of
  manually redefining types. These are well-tested and idiomatic.
language: typescript
category: types
rule_id: UTILITY-TYPES
priority: info
tags:
- utility-types
- reusability
- idioms
---
Leverage Partial, Required, Readonly, Pick, Omit, etc. instead of
manually redefining types. These are well-tested and idiomatic.

## Good

- type PartialEntity = Partial<Entity>;
- type EntityId = Pick<Entity, 'id'>;

## Bad

- type PartialEntity = { id?: number; name?: string; };
