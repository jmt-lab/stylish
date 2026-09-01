---
type: Styleguide Rule
description: "Enum type names use PascalCase. Enum members also use PascalCase to \ndistinguish them from constants."
language: typescript
category: naming
rule_id: TS-ENUM-PASCAL
priority: warn
tags:
- enums
- conventions
---
Enum type names use PascalCase. Enum members also use PascalCase to 
distinguish them from constants.

## Good

- enum EntityType { Player, Enemy, Item }
- enum RenderPass { Shadow, Opaque, Transparent }

## Bad

- enum entityType { player, enemy } // lowercase
- enum RenderPass { SHADOW, OPAQUE } // SCREAMING_SNAKE_CASE
