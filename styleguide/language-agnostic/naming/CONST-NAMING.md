---
type: Styleguide Rule
description: |-
  Constants and macro definitions should use uppercase with underscores
  to clearly distinguish them from variables.
language: language-agnostic
category: naming
rule_id: CONST-NAMING
priority: warn
tags:
- constants
- macros
- conventions
---
Constants and macro definitions should use uppercase with underscores
to clearly distinguish them from variables.

## Good

- MAX_ENTITIES
- ZONEID
- STR_ALLOC_GRAN

## Bad

- maxEntities // Looks like variable
- Zoneid // Inconsistent case
