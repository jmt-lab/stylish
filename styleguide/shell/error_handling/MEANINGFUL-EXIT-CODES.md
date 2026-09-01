---
type: Styleguide Rule
description: Return 0 for success, non-zero for errors. Use different codes for different error types.
language: shell
category: error_handling
rule_id: MEANINGFUL-EXIT-CODES
priority: warn
tags:
- error-handling
- exit-codes
---
Return 0 for success, non-zero for errors. Use different codes for different error types.

## Good

- if [[ ! -f "${file}" ]]; then
  echo "Error: File not found" >&2
  exit 2
fi


## Bad

- if [[ ! -f "${file}" ]]; then
  echo "Error: File not found" >&2
  # No exit
fi

