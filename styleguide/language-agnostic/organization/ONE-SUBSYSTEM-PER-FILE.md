---
type: Styleguide Rule
description: |-
  Files should be focused on a single subsystem or logical component.
  Header and implementation should be paired with matching names.
language: language-agnostic
category: organization
rule_id: ONE-SUBSYSTEM-PER-FILE
priority: warn
tags:
- files
- organization
- modularity
---
Files should be focused on a single subsystem or logical component.
Header and implementation should be paired with matching names.

## Good

- Entity.h / Entity.cpp
- Heap.h / Heap.cpp
- Renderer.h / Renderer.cpp

## Bad

- Utils.cpp // Too generic
- Misc.cpp // Unclear purpose
