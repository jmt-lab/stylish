---
type: Styleguide Rule
description: |-
  When using 'as' type assertions or 'any', explain why the assertion
  is safe and necessary. Type assertions bypass compiler checks and
  need justification.
language: typescript
category: comments
rule_id: TYPE-ASSERTIONS-JUSTIFICATION
priority: error
tags:
- type-safety
- assertions
- justification
---
When using 'as' type assertions or 'any', explain why the assertion
is safe and necessary. Type assertions bypass compiler checks and
need justification.

## Good

- // Safe: we validated the shape with zod schema above const user = data as User;
- // Library types are incorrect; actual return type is string[] const result = legacyFn() as string[];

## Bad

- const user = data as User;
- const x = y as any;
