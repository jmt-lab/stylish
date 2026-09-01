---
type: Styleguide Rule
description: |-
  All input parameters that won't be modified should be marked const.
  This documents intent and prevents accidental modification.
language: language-agnostic
category: const_usage
rule_id: CONST-PARAMETERS
priority: error
tags:
- parameters
- intent
- safety
---
All input parameters that won't be modified should be marked const.
This documents intent and prevents accidental modification.

## Good

- void Process(const Entity* entity, const Vector3& position)

## Bad

- void Process(Entity* entity, Vector3& position) // Unclear if modified
