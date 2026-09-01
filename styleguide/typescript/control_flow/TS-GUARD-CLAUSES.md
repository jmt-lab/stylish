---
type: Styleguide Rule
description: |-
  Place validation checks at function start as guard clauses. Exit
  early on invalid conditions.
language: typescript
category: control_flow
rule_id: TS-GUARD-CLAUSES
priority: warn
tags:
- guards
- nesting
- validation
---
Place validation checks at function start as guard clauses. Exit
early on invalid conditions.

## Good

- if (items.length === 0) return;
if (!config.enabled) return;
processItems(items);

## Bad

- if (items.length > 0) {
  if (config.enabled) {
    processItems(items);
  }
}
