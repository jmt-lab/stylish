---
type: Styleguide Rule
description: |-
  Carmack's assertions map to panic! in Rust. Use panic! or assert!
  for bugs and invariant violations, not for expected failures.
language: rust
category: error_handling
rule_id: PANIC-FOR-PROGRAMMER-ERRORS
priority: error
tags:
- errors
- panic
- assertions
- carmack
---
Carmack's assertions map to panic! in Rust. Use panic! or assert!
for bugs and invariant violations, not for expected failures.

## Good

- assert!(entity_count <= MAX_ENTITIES, "Entity limit exceeded");
- if index >= len { panic!("Index out of bounds"); }

## Bad

- // Don't panic for expected errors
if file_missing { panic!("File not found"); }
