---
type: Styleguide Rule
description: Avoid duplication where the same or similar logic appears in multiple places to avoid maintenance burden. Extract common logic into reusable functions, create traits for common behavior, or use macros for repetitive patterns.
language: rust
category: architecture
rule_id: AVOID-DUPLICATION
priority: error
tags:
- architecture
- maintainability
- code-organization
---
Avoid duplication where the same or similar logic appears in multiple places to avoid maintenance burden. Extract common logic into reusable functions, create traits for common behavior, or use macros for repetitive patterns.

## Good

- fn validate_email(email: &str) -> Result<()> { /* ... */ }
// Used in multiple places


## Bad

- // Same validation logic copied in 5 different functions

