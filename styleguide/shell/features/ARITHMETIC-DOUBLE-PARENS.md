---
type: Styleguide Rule
description: Use (( )) or $(( )) for arithmetic operations instead of expr or let.
language: shell
category: features
rule_id: ARITHMETIC-DOUBLE-PARENS
priority: warn
tags:
- syntax
- arithmetic
- performance
---
Use (( )) or $(( )) for arithmetic operations instead of expr or let.

## Good

- (( i++ ))
- result=$(( a + b ))
- if (( count > 10 )); then

## Bad

- i=`expr $i + 1`
- let i=i+1
