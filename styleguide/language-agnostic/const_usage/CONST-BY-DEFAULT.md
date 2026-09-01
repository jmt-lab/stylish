---
type: Styleguide Rule
description: |-
  Every variable, parameter, and return value should be const/immutable
  unless there is a specific reason for mutability. Opt into mutability,
  don't opt into immutability.
language: language-agnostic
category: const_usage
rule_id: CONST-BY-DEFAULT
priority: error
tags:
- immutability
- safety
- correctness
---
Every variable, parameter, and return value should be const/immutable
unless there is a specific reason for mutability. Opt into mutability,
don't opt into immutability.

## Good

- const int count = entities.size();
- const Entity* GetEntity(const int id) const;

## Bad

- int count = entities.size(); // Never modified
- Entity* GetEntity(int id); // Should be const
