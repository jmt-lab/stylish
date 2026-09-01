---
type: Styleguide Rule
description: |-
  Generic code is harder to read and debug. Use generics sparingly,
  only when the abstraction provides clear value across multiple uses.
language: language-agnostic
category: abstraction
rule_id: CONCRETE-OVER-GENERIC
priority: warn
tags:
- generics
- templates
- clarity
---
Generic code is harder to read and debug. Use generics sparingly,
only when the abstraction provides clear value across multiple uses.

## Good

- // Concrete, clear
void ProcessEntities(Entity* entities, int count)

## Bad

- // Over-generic
template<typename T, typename Policy, typename... Args>
void Process()
