---
type: Styleguide Rule
description: |-
  Use type guards and conditionals to narrow types. TypeScript
  understands typeof, instanceof, and custom type guards.
language: typescript
category: control_flow
rule_id: TS-TYPE-NARROWING
priority: info
tags:
- type-narrowing
- type-guards
- safety
---
Use type guards and conditionals to narrow types. TypeScript
understands typeof, instanceof, and custom type guards.

## Good

- if (typeof value === 'string') {
  return value.toUpperCase(); // value is string
}

## Bad

- return (value as string).toUpperCase(); // Unsafe cast
