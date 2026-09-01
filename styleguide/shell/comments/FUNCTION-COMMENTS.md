---
type: Styleguide Rule
description: Functions should have comments describing their purpose, arguments, and return values.
language: shell
category: comments
rule_id: FUNCTION-COMMENTS
priority: warn
tags:
- comments
- functions
---
Functions should have comments describing their purpose, arguments, and return values.

## Good

- # Process user input and validate format.
# Arguments:
#   $1 - User input string
# Returns:
#   0 on success, 1 on validation failure
process_input() {
  local input="$1"
  # ...
}


## Bad

- process_input() {
  local input="$1"
  # ...
}

