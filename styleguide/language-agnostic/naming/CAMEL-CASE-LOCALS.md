---
type: Styleguide Rule
description: "Local variables and class members should use camelCase starting with \nlowercase letter."
language: language-agnostic
category: naming
rule_id: CAMEL-CASE-LOCALS
priority: info
tags:
- variables
- members
- conventions
---
Local variables and class members should use camelCase starting with 
lowercase letter.

## Good

- entityNumber
- frameCount
- deltaTime

## Bad

- EntityNumber // PascalCase for local
- entity_number // snake_case
