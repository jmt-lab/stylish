---
type: Styleguide Rule
description: |-
  When iterating over a collection without modifying it, use const
  iterators to prevent accidental modification.
language: language-agnostic
category: const_usage
rule_id: CONST-ITERATORS
priority: warn
tags:
- iteration
- collections
- safety
---
When iterating over a collection without modifying it, use const
iterators to prevent accidental modification.

## Good

- for (const auto& entity : entities)
- const_iterator it = entities.begin();

## Bad

- for (auto& entity : entities) // Not modifying, should be const
