---
type: Styleguide Rule
description: |-
  Avoid vague suffixes like Manager, Service, Factory, Helper, Util, and
  Handler on type names. Name what the thing is or does (Bookings,
  Dispatcher, ConnectionPool, FooBuilder).
language: rust
category: naming
rule_id: AVOID-WEASEL-WORDS
priority: warn
tags:
- naming
- types
- clarity
- beautiful-rust
---
Avoid vague suffixes like Manager, Service, Factory, Helper, Util, and
Handler on type names. Name what the thing is or does (Bookings,
Dispatcher, ConnectionPool, FooBuilder).

## Good

- pub struct Bookings { ... }
- pub struct ConnectionPool { ... }
- pub struct RequestBuilder { ... }

## Bad

- pub struct BookingManager { ... }
- pub struct ConnectionService { ... }
- pub struct RequestFactory { ... }
