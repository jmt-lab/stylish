---
type: Styleguide Rule
description: |-
  For dependencies prefer, in order: concrete types, generics over narrow
  traits, then dyn Trait wrapped in your own struct (e.g.
  struct DynStore(Arc<dyn Store>)). Don't port interface-everything designs
  (IDatabase) into Rc<dyn Database> by default.
language: rust
category: api_design
rule_id: PREFER-CONCRETE-THEN-GENERIC-THEN-DYN
priority: info
tags:
- api-design
- generics
- dyn
- dependency-injection
- beautiful-rust
---
For dependencies prefer, in order: concrete types, generics over narrow
traits, then dyn Trait wrapped in your own struct (e.g.
struct DynStore(Arc<dyn Store>)). Don't port interface-everything designs
(IDatabase) into Rc<dyn Database> by default.

## Good

- pub struct Bookings { db: Postgres }
- pub struct Bookings<S: Store> { store: S }
- pub struct DynStore(Arc<dyn Store + Send + Sync>); // when runtime selection is needed

## Bad

- pub struct Bookings { db: Rc<dyn IDatabase> } // only ever one implementation
