---
type: Styleguide Rule
description: Always quote variables and command substitutions unless you explicitly need word splitting or globbing. Unquoted expansions break with spaces in values and can cause dangerous behavior with paths.
language: shell
category: variables
rule_id: QUOTE-EXPANSIONS
priority: error
tags:
- variables
- quoting
- safety
---
Always quote variables and command substitutions unless you explicitly need word splitting or globbing. Unquoted expansions break with spaces in values and can cause dangerous behavior with paths.

## Good

- echo "${name}"  # Prevents word splitting
- rm -rf "${dir}"  # Safe even with spaces
- if [[ "${status}" == "success" ]]; then
- if [[ "${count}" -gt 0 ]]; then

## Bad

- echo ${name}  # Breaks with spaces
- rm -rf ${dir}  # Dangerous with spaces in path
- for file in $(ls); do  # Word splitting issues
- echo $my_var
- if [[ $count -gt 0 ]]; then
