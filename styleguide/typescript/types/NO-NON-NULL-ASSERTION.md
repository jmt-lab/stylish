---
type: Styleguide Rule
description: |-
  Avoid '!' operator - it disables null checking. Use type guards or
  optional chaining instead. Document if truly necessary.
language: typescript
category: types
rule_id: NO-NON-NULL-ASSERTION
priority: warn
tags:
- null-safety
- assertions
- safety
---
Avoid '!' operator - it disables null checking. Use type guards or
optional chaining instead. Document if truly necessary.

## Good

- if (entity) { process(entity); }
- entity?.process();

## Bad

- process(entity!); // Unsafe assertion
