---
type: Styleguide Rule
description: Use semicolons consistently per project preference. Configure Prettier.
language: typescript
category: formatting
rule_id: TS-FMT-SEMICOLONS
priority: info
tags:
- semicolons
- consistency
---
Use semicolons consistently per project preference. Configure Prettier.

## Good

- const x = 1; // If project uses semicolons
- const x = 1 // If project omits semicolons

## Bad

- // Mixing both styles in same project
