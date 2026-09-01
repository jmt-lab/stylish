---
type: Styleguide Rule
description: |-
  Check error conditions at function start and return early. Keeps
  happy path at base indentation level.
language: typescript
category: control_flow
rule_id: TS-EARLY-RETURN
priority: warn
tags:
- returns
- errors
- clarity
---
Check error conditions at function start and return early. Keeps
happy path at base indentation level.

## Good

- if (!entity) return null;
if (!entity.isValid()) return null;
// Happy path

## Bad

- if (entity) {
  if (entity.isValid()) {
    // Happy path nested
  }
}
