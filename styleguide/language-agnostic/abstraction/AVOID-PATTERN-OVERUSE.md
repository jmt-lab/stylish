---
type: Styleguide Rule
description: |-
  Design patterns solve specific problems. Don't apply patterns because
  they're patterns. Apply them when they solve a real problem.
language: language-agnostic
category: abstraction
rule_id: AVOID-PATTERN-OVERUSE
priority: info
tags:
- patterns
- design
- complexity
---
Design patterns solve specific problems. Don't apply patterns because
they're patterns. Apply them when they solve a real problem.

## Good

- // Simple factory when needed
Entity* CreateEntity(type)

## Bad

- // Unnecessary pattern application
AbstractFactoryBuilderStrategyProxy...
