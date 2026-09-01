---
type: Styleguide Rule
description: |-
  Group related feature flags, use descriptive names, and document
  what each feature enables.
language: rust
category: organization
rule_id: FEATURE-FLAGS-ORGANIZED
priority: info
tags:
- organization
- features
- cargo
---
Group related feature flags, use descriptive names, and document
what each feature enables.

## Good

- [features]
default = ["std"]
# Rendering backends
vulkan = ["ash"]
opengl = ["gl"]

## Bad

- [features]
feature1 = []
feature2 = []
my_thing = []
