---
type: Styleguide Rule
description: |-
  Do not prefix variables with type information. Modern IDEs show types,
  and type prefixes add noise without value.
language: language-agnostic
category: naming
rule_id: NO-HUNGARIAN
priority: warn
tags:
- variables
- antipattern
---
Do not prefix variables with type information. Modern IDEs show types,
and type prefixes add noise without value.

## Good

- entityCount
- position
- isValid

## Bad

- iEntityCount // Type prefix
- pPosition // Pointer prefix
- bIsValid // Boolean prefix
