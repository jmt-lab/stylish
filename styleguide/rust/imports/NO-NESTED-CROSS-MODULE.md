---
type: Styleguide Rule
description: Avoid mixing modules using nested paths like `use std::{collections::HashMap, fs::File}`. Nested paths are acceptable when all items share the same parent module (see NESTED-SAME-MODULE). This rule applies only when mixing items from different submodules in a single use statement.
language: rust
category: imports
rule_id: NO-NESTED-CROSS-MODULE
priority: error
tags:
- imports
- modules
- readability
---
Avoid mixing modules using nested paths like `use std::{collections::HashMap, fs::File}`. Nested paths are acceptable when all items share the same parent module (see NESTED-SAME-MODULE). This rule applies only when mixing items from different submodules in a single use statement.

## Good

- use std::collections::HashMap;
- use std::fs::File;

## Bad

- use std::{collections::HashMap, fs::File};
