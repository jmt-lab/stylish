---
type: Styleguide Rule
description: Always check the exit status of commands that can fail.
language: shell
category: error_handling
rule_id: CHECK-EXIT-STATUS
priority: error
tags:
- error-handling
- safety
---
Always check the exit status of commands that can fail.

## Good

- if ! cp source dest; then
  echo "Error: Failed to copy file" >&2
  exit 1
fi


## Bad

- cp source dest
# No error checking

