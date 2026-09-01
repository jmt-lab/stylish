---
type: Styleguide Rule
description: Use "${array[@]}" to expand all elements as separate words, not "${array[*]}".
language: shell
category: variables
rule_id: ARRAY-EXPANSION
priority: error
tags:
- variables
- arrays
- expansion
---
Use "${array[@]}" to expand all elements as separate words, not "${array[*]}".

## Good

- process_files "${files[@]}"  # Each element separate
- for item in "${array[@]}"; do

## Bad

- process_files "${files[*]}"  # All elements as one word
- for item in ${array[@]}; do  # Unquoted
