---
type: Styleguide Rule
description: |-
  Methods that don't modify object state should be marked const. This
  enables use with const references and documents behavior.
language: language-agnostic
category: const_usage
rule_id: CONST-METHODS
priority: error
tags:
- methods
- classes
- correctness
---
Methods that don't modify object state should be marked const. This
enables use with const references and documents behavior.

## Good

- const char* GetName() const;
- float GetHealth() const;

## Bad

- const char* GetName(); // Should be const method
