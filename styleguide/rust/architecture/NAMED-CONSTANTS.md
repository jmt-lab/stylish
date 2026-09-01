---
type: Styleguide Rule
description: Replace unexplained literals with named constants or domain-specific types for readability and maintainability. Use descriptive names, enums for discrete states, configuration structs, and domain-specific types for type safety.
language: rust
category: architecture
rule_id: NAMED-CONSTANTS
priority: warn
tags:
- readability
- maintainability
- code-organization
---
Replace unexplained literals with named constants or domain-specific types for readability and maintainability. Use descriptive names, enums for discrete states, configuration structs, and domain-specific types for type safety.

## Good

- const MAX_RETRY_ATTEMPTS: u32 = 3;
const TIMEOUT_MS: u64 = 5000;

- struct Money(Decimal);
struct Duration(u64);


## Bad

- if attempts > 3 { return; }
sleep(5000);

