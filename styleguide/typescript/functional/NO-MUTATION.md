---
type: Styleguide Rule
description: |-
  Use spread operator and array methods to create new values instead of
  mutating existing ones. Transform data by returning new values, not
  mutating inputs. This makes data flow explicit and prevents
  action-at-a-distance bugs.
language: typescript
category: functional
rule_id: NO-MUTATION
priority: warn
tags:
- immutability
- mutation
- spread
- data-flow
- return-values
---
Use spread operator and array methods to create new values instead of
mutating existing ones. Transform data by returning new values, not
mutating inputs. This makes data flow explicit and prevents
action-at-a-distance bugs.

## Good

- const updated = { ...entity, health: entity.health - damage };
- const added = [...items, newItem];
- function applyDamage(entity: Entity, dmg: number): Entity {
  return { ...entity, health: entity.health - dmg };
}

## Bad

- entity.health -= damage;
- items.push(newItem);
- function applyDamage(entity: Entity, dmg: number): void {
  entity.health -= dmg;
}
