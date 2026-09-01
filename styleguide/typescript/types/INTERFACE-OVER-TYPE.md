---
type: Styleguide Rule
description: |-
  Use interfaces for object types, type aliases for unions/intersections.
  Interfaces are more extensible and have better error messages.
language: typescript
category: types
rule_id: INTERFACE-OVER-TYPE
priority: warn
tags:
- interfaces
- types
- style
---
Use interfaces for object types, type aliases for unions/intersections.
Interfaces are more extensible and have better error messages.

## Good

- interface Entity { id: number; name: string; }
- type Result = Success | Error;

## Bad

- type Entity = { id: number; name: string; };
