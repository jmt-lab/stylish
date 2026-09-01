---
type: Styleguide Rule
description: |-
  When a function moves a value, consider naming that makes this clear
  (into_*, take_*, consume_*).
language: rust
category: ownership
rule_id: MOVE-SEMANTICS-CLEAR
priority: info
tags:
- ownership
- naming
- clarity
---
When a function moves a value, consider naming that makes this clear
(into_*, take_*, consume_*).

## Good

- fn into_inner(self) -> T // Clear: consumes self
- fn take_buffer(self) -> Vec<u8> // Clear: moves out buffer

## Bad

- fn inner(self) -> T // Unclear that self is consumed
