---
type: Styleguide Rule
description: |-
  When transforming data, return a new value instead of mutating the
  input. This makes data flow clear and prevents bugs.
language: language-agnostic
category: functional_patterns
rule_id: RETURN-NEW-VALUES
priority: warn
tags:
- immutability
- data-flow
- clarity
---
When transforming data, return a new value instead of mutating the
input. This makes data flow clear and prevents bugs.

## Good

- Entity updated = ApplyDamage(entity, damage);

## Bad

- ApplyDamage(&entity, damage); // Mutates in place
