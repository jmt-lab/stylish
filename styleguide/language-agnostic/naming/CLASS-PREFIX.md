---
type: Styleguide Rule
description: "Classes and types should use a consistent lowercase prefix followed by \nPascalCase. This prevents naming collisions and makes code origin obvious."
language: language-agnostic
category: naming
rule_id: CLASS-PREFIX
priority: warn
tags:
- classes
- types
- namespacing
---
Classes and types should use a consistent lowercase prefix followed by 
PascalCase. This prevents naming collisions and makes code origin obvious.

## Good

- idStr // id Software string class
- idVec3 // id Software 3D vector
- idEntity // id Software entity class

## Bad

- String // Generic, collision-prone
- Vec3 // No namespace
