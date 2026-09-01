---
type: Styleguide Rule
description: "File names should use kebab-case (lowercase with hyphens). This is \nstandard in TypeScript projects and avoids case-sensitivity issues."
language: typescript
category: naming
rule_id: TS-FILE-KEBAB
priority: warn
tags:
- files
- conventions
---
File names should use kebab-case (lowercase with hyphens). This is 
standard in TypeScript projects and avoids case-sensitivity issues.

## Good

- render-entity.ts
- entity-manager.ts
- vector-math.ts

## Bad

- RenderEntity.ts // PascalCase
- entity_manager.ts // snake_case
- vectorMath.ts // camelCase
