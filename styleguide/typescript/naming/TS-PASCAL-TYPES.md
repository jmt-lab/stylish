---
type: Styleguide Rule
description: "All type definitions including classes, interfaces, type aliases, and \nenums should use PascalCase."
language: typescript
category: naming
rule_id: TS-PASCAL-TYPES
priority: error
tags:
- types
- classes
- interfaces
- conventions
---
All type definitions including classes, interfaces, type aliases, and 
enums should use PascalCase.

## Good

- class RenderEntity {}
- interface Vector3 {}
- type EntityId = number;

## Bad

- class renderEntity {} // camelCase
- interface vector3 {} // lowercase
- type entityId = number; // camelCase
