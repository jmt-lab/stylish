---
type: Styleguide Rule
description: Keep related functions near each other with section comments.
language: shell
category: organization
rule_id: GROUP-RELATED-FUNCTIONS
priority: info
tags:
- organization
- functions
---
Keep related functions near each other with section comments.

## Good

- # File operations
read_config() { ... }
write_config() { ... }

# Validation functions
validate_input() { ... }
validate_output() { ... }


## Bad

- read_config() { ... }
validate_input() { ... }
write_config() { ... }
validate_output() { ... }

