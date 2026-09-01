---
type: Styleguide Rule
description: Use trap to ensure cleanup happens even on errors or interrupts.
language: shell
category: error_handling
rule_id: TRAP-CLEANUP
priority: info
tags:
- error-handling
- cleanup
- resources
---
Use trap to ensure cleanup happens even on errors or interrupts.

## Good

- cleanup() {
  rm -f "${temp_file}"
}
trap cleanup EXIT

temp_file=$(mktemp)


## Bad

- temp_file=$(mktemp)
# Do work
rm -f "${temp_file}"  # May not run if script exits early

