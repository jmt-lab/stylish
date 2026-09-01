---
type: Styleguide Rule
description: |-
  Templates are appropriate for containers, math types, and low-level
  utilities. Avoid in business logic where concrete types are clearer.
language: language-agnostic
category: abstraction
rule_id: TEMPLATES-UTILITY-ONLY
priority: warn
tags:
- templates
- scope
- appropriateness
---
Templates are appropriate for containers, math types, and low-level
utilities. Avoid in business logic where concrete types are clearer.

## Good

- template<class T> class Array { }; // Container
- template<typename T> T Max(T a, T b); // Utility

## Bad

- template<typename Policy> class GameLogic { }; // Wrong level
