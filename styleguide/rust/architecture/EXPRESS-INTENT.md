---
type: Styleguide Rule
description: Code should clearly express its purpose and intent, making it easy for readers to understand. Use clear descriptive names, split complex expressions into intermediate steps, and replace primitive types with domain-specific types where appropriate.
language: rust
category: architecture
rule_id: EXPRESS-INTENT
priority: warn
tags:
- readability
- simplicity
- maintainability
---
Code should clearly express its purpose and intent, making it easy for readers to understand. Use clear descriptive names, split complex expressions into intermediate steps, and replace primitive types with domain-specific types where appropriate.

## Good

- let is_eligible = age >= 18 && has_valid_id;
if is_eligible { /* ... */ }


## Bad

- if x >= 18 && y { /* ... */ }

