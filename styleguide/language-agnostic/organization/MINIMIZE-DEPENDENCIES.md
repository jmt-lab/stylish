---
type: Styleguide Rule
description: |-
  Reduce coupling between files. Use forward declarations where possible
  instead of includes. This improves compile times and modularity.
language: language-agnostic
category: organization
rule_id: MINIMIZE-DEPENDENCIES
priority: warn
tags:
- dependencies
- compilation
- modularity
---
Reduce coupling between files. Use forward declarations where possible
instead of includes. This improves compile times and modularity.

## Good

- // Forward declare instead of include
class Entity;
void Process(Entity* e);

## Bad

- #include "Everything.h" // Kitchen sink include
