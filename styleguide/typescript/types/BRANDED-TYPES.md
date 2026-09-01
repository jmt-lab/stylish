---
type: Styleguide Rule
description: |-
  Create branded types for domain-specific primitives to prevent mixing
  incompatible values (e.g., UserId vs EntityId).
language: typescript
category: types
rule_id: BRANDED-TYPES
priority: info
tags:
- domain-modeling
- type-safety
- primitives
---
Create branded types for domain-specific primitives to prevent mixing
incompatible values (e.g., UserId vs EntityId).

## Good

- type UserId = number & { readonly __brand: 'UserId' };
- type EntityId = number & { readonly __brand: 'EntityId' };

## Bad

- type UserId = number; type EntityId = number; // Can be mixed
