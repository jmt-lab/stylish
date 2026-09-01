---
type: Styleguide Rule
description: |-
  TODO comments should include who, when, and why. Include issue
  tracker references when applicable.
language: language-agnostic
category: comments
rule_id: TODO-WITH-CONTEXT
priority: info
tags:
- todo
- maintenance
- tracking
---
TODO comments should include who, when, and why. Include issue
tracker references when applicable.

## Good

- // TODO(carmack, 2023-05-15): Optimize this for SSE4
// See issue #1234

## Bad

- // TODO: fix this
- // HACK
