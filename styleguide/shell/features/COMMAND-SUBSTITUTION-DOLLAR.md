---
type: Styleguide Rule
description: Use $(command) instead of backticks for command substitution. Backticks are deprecated — they nest poorly, are harder to read, and require escaping. $() is more readable and nests cleanly.
language: shell
category: features
rule_id: COMMAND-SUBSTITUTION-DOLLAR
priority: error
tags:
- syntax
- readability
- nesting
- deprecated
---
Use $(command) instead of backticks for command substitution. Backticks are deprecated — they nest poorly, are harder to read, and require escaping. $() is more readable and nests cleanly.

## Good

- result=$(ls -l)
- outer=$(echo "inner=$(date)")
- current_date=$(date +%Y-%m-%d)
- files=$(find . -name "*.sh")

## Bad

- result=`ls -l`
- outer=`echo "inner=\`date\`"`
- current_date=`date +%Y-%m-%d`
