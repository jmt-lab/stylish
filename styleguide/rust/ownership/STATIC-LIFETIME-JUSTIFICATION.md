---
type: Styleguide Rule
description: |-
  'static lifetime means data lives for entire program. Only use when
  truly necessary (string literals, leaked allocations, globals).
language: rust
category: ownership
rule_id: STATIC-LIFETIME-JUSTIFICATION
priority: warn
tags:
- ownership
- lifetimes
- static
---
'static lifetime means data lives for entire program. Only use when
truly necessary (string literals, leaked allocations, globals).

## Good

- const NAME: &'static str = "Entity"; // Literal, fine
- fn spawn_thread<F: FnOnce() + Send + 'static>(f: F) // Thread needs 'static

## Bad

- // Don't require 'static unnecessarily
fn process(data: &'static [u8]) // Overly restrictive
