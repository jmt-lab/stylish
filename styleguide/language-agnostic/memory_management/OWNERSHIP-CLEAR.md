---
type: Styleguide Rule
description: |-
  Every allocation should have clear ownership. Document who is
  responsible for freeing memory.
language: language-agnostic
category: memory_management
rule_id: OWNERSHIP-CLEAR
priority: error
tags:
- ownership
- documentation
- safety
---
Every allocation should have clear ownership. Document who is
responsible for freeing memory.

## Good

- // Returns owned pointer, caller must free
Entity* CreateEntity();
- // Borrowed pointer, don't free
void Process(const Entity* entity);

## Bad

- Entity* GetEntity(); // Who owns this?
