---
type: Styleguide Rule
description: |-
  TODO comments should include who, when, why, and issue tracker
  references when applicable.
language: rust
category: comments
rule_id: TODO-WITH-CONTEXT
priority: info
tags:
- todo
- maintenance
- carmack
---
TODO comments should include who, when, why, and issue tracker
references when applicable.

## Good

- // TODO(username, 2024-12-17): Optimize for SIMD
// See issue #1234
- // TODO: Add support for HDR rendering (blocked on #456)

## Bad

- // TODO: fix this
- // HACK
