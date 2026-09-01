---
type: Styleguide Rule
description: Always quote command substitutions to prevent word splitting and globbing of the result.
language: shell
category: commands
rule_id: QUOTE-COMMAND-SUBSTITUTION
priority: error
tags:
- quoting
- robustness
- google
---
Always quote command substitutions to prevent word splitting and globbing of the result.

## Good

- current_dir="$(pwd)"

- files="$(find . -name '*.txt')"

- count="$(wc -l < file.txt)"


## Bad

- current_dir=$(pwd)
# Unquoted - subject to word splitting

- files=$(find . -name '*.txt')
# Could break with spaces in filenames

