---
type: Styleguide Rule
description: Avoid eval. If absolutely necessary for dynamic variable names, never use with untrusted input and document the justification.
language: shell
category: features
rule_id: AVOID-EVAL-FEATURES
priority: error
tags:
- security
- safety
- maintainability
---
Avoid eval. If absolutely necessary for dynamic variable names, never use with untrusted input and document the justification.

## Good

- commands=("ls" "pwd" "date")
for cmd in "${commands[@]}"; do
  "${cmd}"
done

- # Use indirect expansion instead of eval
var_name="MY_VAR"
echo "${!var_name}"


## Bad

- eval "${user_input}"
- eval "cmd_${suffix}"
