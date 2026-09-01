---
type: Styleguide Rule
description: Check that required arguments are provided and valid.
language: shell
category: error_handling
rule_id: VALIDATE-ARGS
priority: warn
tags:
- error-handling
- validation
- functions
---
Check that required arguments are provided and valid.

## Good

- process_file() {
  local file="$1"
  if [[ -z "${file}" ]]; then
    echo "Error: File argument required" >&2
    return 1
  fi
  # ...
}


## Bad

- process_file() {
  local file="$1"
  # No validation
  cat "${file}"
}

