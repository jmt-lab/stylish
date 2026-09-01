---
type: Styleguide Rule
description: "Variables, function names, and method names should use camelCase starting \nwith lowercase letter. This is standard TypeScript convention."
language: typescript
category: naming
rule_id: TS-CAMEL-VARS
priority: error
tags:
- variables
- functions
- conventions
---
Variables, function names, and method names should use camelCase starting 
with lowercase letter. This is standard TypeScript convention.

## Good

- const entityCount = 10;
- function renderScene() {}
- const deltaTime = 0.016;

## Bad

- const EntityCount = 10; // PascalCase
- function RenderScene() {} // PascalCase
- const delta_time = 0.016; // snake_case
