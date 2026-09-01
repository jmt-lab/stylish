---
type: Styleguide Rule
description: Declare all variables inside functions with local (or declare) to avoid polluting global scope, prevent unexpected state mutations, and keep functions self-contained.
language: shell
category: features
rule_id: LOCAL-IN-FUNCTIONS
priority: error
tags:
- scope
- functions
- state-management
- variables
---
Declare all variables inside functions with local (or declare) to avoid polluting global scope, prevent unexpected state mutations, and keep functions self-contained.

## Good

- process_file() {
  local file="$1"
  local result
  result=$(process "${file}")
}

- my_function() {
  local result="value"
  echo "${result}"
}


## Bad

- process_file() {
  file="$1"
  result=$(process "${file}")
}

- my_function() {
  result="value"  # Global variable
  echo "${result}"
}

