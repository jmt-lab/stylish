---
type: Styleguide Rule
description: |-
  Expensive validation should use debug_assert! to run only in debug
  builds. Critical safety checks use assert! (always runs).
language: rust
category: error_handling
rule_id: DEBUG-ASSERT-EXPENSIVE
priority: warn
tags:
- assertions
- debug
- performance
---
Expensive validation should use debug_assert! to run only in debug
builds. Critical safety checks use assert! (always runs).

## Good

- debug_assert!(is_sorted(&array)); // Expensive check
- assert!(!ptr.is_null()); // Critical safety check

## Bad

- assert!(is_sorted(&array)); // Expensive, runs in release
