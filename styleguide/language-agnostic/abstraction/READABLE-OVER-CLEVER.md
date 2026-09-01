---
type: Styleguide Rule
description: |-
  Clever code is impressive but unmaintainable. Write code that future
  you (or teammates) can understand at 3am debugging a crash.
language: language-agnostic
category: abstraction
rule_id: READABLE-OVER-CLEVER
priority: warn
tags:
- readability
- cleverness
- maintenance
---
Clever code is impressive but unmaintainable. Write code that future
you (or teammates) can understand at 3am debugging a crash.

## Good

- // Clear
if (x > 0 && x < max) { ... }

## Bad

- // Clever
if ((unsigned)x < (unsigned)max) { ... }
