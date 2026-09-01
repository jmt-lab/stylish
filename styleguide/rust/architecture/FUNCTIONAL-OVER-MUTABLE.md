---
type: Styleguide Rule
description: Replace mutable status variables and boolean flags with functional constructs, iterator combinators, and enum-based state management to prevent invalid states and improve clarity.
language: rust
category: architecture
rule_id: FUNCTIONAL-OVER-MUTABLE
priority: warn
tags:
- architecture
- simplicity
- safety
---
Replace mutable status variables and boolean flags with functional constructs, iterator combinators, and enum-based state management to prevent invalid states and improve clarity.

## Good

- items.iter().any(|item| item.is_valid())

- enum State { Pending, Active, Completed }


## Bad

- let mut found = false;
for item in items {
    if item.is_valid() { found = true; break; }
}

