---
type: Styleguide Rule
description: Always use ${var} instead of $var for clarity and to avoid ambiguity.
language: shell
category: variables
rule_id: BRACE-EXPANSION
priority: warn
tags:
- variables
- expansion
- clarity
---
Always use ${var} instead of $var for clarity and to avoid ambiguity.

## Good

- echo "${name}"  # Clear boundaries
- file="${prefix}_data.txt"
- echo "${array[@]}"

## Bad

- echo "$name"  # Ambiguous in complex expressions
- file="$prefix_data.txt"  # Is it $prefix_data or ${prefix}_data?
