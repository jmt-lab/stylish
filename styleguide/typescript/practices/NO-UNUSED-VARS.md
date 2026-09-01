---
type: Styleguide Rule
description: |-
  Enable noUnusedLocals and noUnusedParameters. Unused code is dead
  code. Remove it or prefix with underscore if intentionally unused.
language: typescript
category: practices
rule_id: NO-UNUSED-VARS
priority: error
tags:
- unused
- dead-code
- cleanup
---
Enable noUnusedLocals and noUnusedParameters. Unused code is dead
code. Remove it or prefix with underscore if intentionally unused.

## Good

- function process(_unused: string, used: number) { return used; }

## Bad

- const unused = getValue(); // Never used
