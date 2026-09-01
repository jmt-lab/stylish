---
type: Styleguide Rule
description: |-
  For collections that are usually small, use SmallVec to avoid
  allocations for the common case.
language: rust
category: memory
rule_id: SMALLVEC-SMALL-COLLECTIONS
priority: info
tags:
- memory
- optimization
- collections
---
For collections that are usually small, use SmallVec to avoid
allocations for the common case.

## Good

- use smallvec::SmallVec;
// Usually has 0-4 items
type SmallEntityVec = SmallVec<[Entity; 4]>;

## Bad

- type EntityVec = Vec<Entity>; // Always heap allocates
