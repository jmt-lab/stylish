---
type: Styleguide Rule
description: |-
  Don't create abstractions prematurely to avoid duplication. Wait until
  you have 3+ similar cases, then abstract. Early abstraction often wrong.
language: language-agnostic
category: abstraction
rule_id: DUPLICATION-VS-ABSTRACTION
priority: info
tags:
- duplication
- abstraction
- timing
---
Don't create abstractions prematurely to avoid duplication. Wait until
you have 3+ similar cases, then abstract. Early abstraction often wrong.

## Good

- // Duplicate twice, then abstract on third occurrence

## Bad

- // Abstract after seeing pattern once (often wrong)
