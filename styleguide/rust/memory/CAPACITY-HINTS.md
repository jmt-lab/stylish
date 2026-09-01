---
type: Styleguide Rule
description: |-
  When you know approximate collection size, use with_capacity to
  avoid reallocation.
language: rust
category: memory
rule_id: CAPACITY-HINTS
priority: warn
tags:
- memory
- performance
- allocations
---
When you know approximate collection size, use with_capacity to
avoid reallocation.

## Good

- let mut entities = Vec::with_capacity(entity_count);
- let mut map = HashMap::with_capacity(expected_size);

## Bad

- let mut entities = Vec::new(); // Will reallocate during push
