---
type: Styleguide Rule
description: Functions should have a single, clear purpose. Break complex functions into smaller ones.
language: shell
category: organization
rule_id: ONE-TASK-PER-FUNCTION
priority: warn
tags:
- organization
- functions
- clarity
---
Functions should have a single, clear purpose. Break complex functions into smaller ones.

## Good

- validate_input() { ... }
process_data() { ... }
write_output() { ... }


## Bad

- do_everything() {
  # Validates, processes, and writes in one function
}

