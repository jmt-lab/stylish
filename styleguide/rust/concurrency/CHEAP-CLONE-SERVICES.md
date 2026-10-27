---
type: Styleguide Rule
description: |-
  Heavyweight shared services (clients, pools, caches) implement a cheap
  Clone by wrapping their state in Arc<Inner>, so callers can clone handles
  freely instead of wrapping the service in Arc themselves.
language: rust
category: concurrency
rule_id: CHEAP-CLONE-SERVICES
priority: info
tags:
- concurrency
- arc
- services
- beautiful-rust
---
Heavyweight shared services (clients, pools, caches) implement a cheap
Clone by wrapping their state in Arc<Inner>, so callers can clone handles
freely instead of wrapping the service in Arc themselves.

## Good

- #[derive(Clone)]
pub struct Client { inner: Arc<ClientInner> }

## Bad

- pub struct Client { pool: Pool, config: Config }
// every caller writes Arc<Client> and the type leaks into signatures
