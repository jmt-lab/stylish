---
type: Styleguide Rule
description: |-
  Types larger than a few KB should be boxed to avoid stack issues
  and reduce move costs.
language: rust
category: memory
rule_id: BOX-LARGE-TYPES
priority: warn
tags:
- memory
- stack
- safety
---
Types larger than a few KB should be boxed to avoid stack issues
and reduce move costs.

## Good

- struct Large([u8; 1_000_000]);
let large = Box::new(Large([0; 1_000_000]));

## Bad

- let large = Large([0; 1_000_000]); // Stack overflow risk
