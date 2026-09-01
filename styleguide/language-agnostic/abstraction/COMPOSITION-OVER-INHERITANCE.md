---
type: Styleguide Rule
description: |-
  Deep inheritance hierarchies are brittle and hard to modify. Prefer
  composition and simple inheritance hierarchies (1-2 levels).
language: language-agnostic
category: abstraction
rule_id: COMPOSITION-OVER-INHERITANCE
priority: warn
tags:
- composition
- inheritance
- design
---
Deep inheritance hierarchies are brittle and hard to modify. Prefer
composition and simple inheritance hierarchies (1-2 levels).

## Good

- // Composition
class Entity {
    RenderComponent render;
    PhysicsComponent physics;
};

## Bad

- // Deep inheritance
Object -> Actor -> Character -> Enemy -> FlyingEnemy -> Boss
