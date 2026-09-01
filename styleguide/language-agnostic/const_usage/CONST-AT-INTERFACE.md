---
type: Styleguide Rule
description: |-
  Public APIs should be especially rigorous about const correctness as
  it becomes part of the contract with callers.
language: language-agnostic
category: const_usage
rule_id: CONST-AT-INTERFACE
priority: error
tags:
- api
- interfaces
- contracts
---
Public APIs should be especially rigorous about const correctness as
it becomes part of the contract with callers.

## Good

- // Public API with clear const contract
const char* GetName() const;

## Bad

- // Unclear mutability contract
char* GetName();
