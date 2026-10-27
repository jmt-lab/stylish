---
type: Styleguide Rule
description: |-
  Don't nest type parameters on service-level public types. Service<Backend>
  is fine; Service<Backend<Store<Cache>>> pushes complexity onto every user.
  Hide inner choices behind a concrete type or a dyn wrapper.
language: rust
category: api_design
rule_id: NO-NESTED-GENERIC-SERVICES
priority: info
tags:
- api-design
- generics
- simplicity
- beautiful-rust
---
Don't nest type parameters on service-level public types. Service<Backend>
is fine; Service<Backend<Store<Cache>>> pushes complexity onto every user.
Hide inner choices behind a concrete type or a dyn wrapper.

## Good

- pub struct Client<T: Transport> { transport: T }

## Bad

- pub struct Client<T: Transport<C: Codec<B: Buffer>>> { ... }
- let client: Client<Http<Json<PooledBuffer>>> = ...;
