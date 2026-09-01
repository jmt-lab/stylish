---
type: Styleguide Rule
description: |-
  TODO comments should include author, date, and reason. Link to issue
  tracker when applicable.
language: typescript
category: comments
rule_id: TODO-WITH-CONTEXT
priority: info
tags:
- todo
- maintenance
- tracking
---
TODO comments should include author, date, and reason. Link to issue
tracker when applicable.

## Good

- // TODO(jcarmack, 2024-01-15): Optimize with SIMD when available // See issue #1234
- // TODO: Remove after TypeScript 5.3 migration (provides native support)

## Bad

- // TODO: fix this
- // HACK
