---
type: Styleguide Rule
description: |-
  Use a newtype instead of a type alias when the type has notable
  semantic differences from the underlying type, warrants its own API, may
  need its representation changed later, or could easily be mixed up with
  other values of the same underlying type.
language: rust
category: types
rule_id: NEWTYPE-OVER-ALIAS
priority: warn
tags:
- types
- newtype
- type-safety
- google-style
---
Use a newtype instead of a type alias when the type has notable
semantic differences from the underlying type, warrants its own API, may
need its representation changed later, or could easily be mixed up with
other values of the same underlying type.

## Good

- pub struct UserId(u64);
pub struct OrderId(u64);

fn cancel(user: UserId, order: OrderId) { ... }

## Bad

- pub type UserId = u64;
pub type OrderId = u64;

cancel(order_id, user_id); // swapped arguments still compile
