---
type: Styleguide Rule
description: |-
  Transform data by returning new values rather than mutating inputs.
  Makes data flow explicit and prevents action-at-a-distance bugs.
language: python
category: functional
rule_id: AVOID-MUTATION
priority: warn
tags:
- immutability
- data-flow
- clarity
---
Transform data by returning new values rather than mutating inputs.
Makes data flow explicit and prevents action-at-a-distance bugs.

## Good

- def apply_damage(entity: Entity, damage: int) -> Entity:
    return Entity(entity.name, entity.hp - damage)

## Bad

- def apply_damage(entity: Entity, damage: int) -> None:
    entity.hp -= damage  # Mutation
