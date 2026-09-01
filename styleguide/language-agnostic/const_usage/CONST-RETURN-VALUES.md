---
type: Styleguide Rule
description: |-
  Return const pointers or references when the caller should not modify
  the returned data.
language: language-agnostic
category: const_usage
rule_id: CONST-RETURN-VALUES
priority: warn
tags:
- return-values
- safety
- intent
---
Return const pointers or references when the caller should not modify
the returned data.

## Good

- const Entity* FindEntity(int id) const;
- const Config& GetConfig() const;

## Bad

- Entity* FindEntity(int id) const; // Should return const*
