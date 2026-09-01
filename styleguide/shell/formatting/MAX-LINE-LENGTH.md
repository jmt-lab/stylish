---
type: Styleguide Rule
description: Lines should not exceed 80 characters. Use line continuation for long commands.
language: shell
category: formatting
rule_id: MAX-LINE-LENGTH
priority: warn
tags:
- formatting
- line-length
---
Lines should not exceed 80 characters. Use line continuation for long commands.

## Good

- long_command --option1 value1 \
  --option2 value2 \
  --option3 value3


## Bad

- long_command --option1 value1 --option2 value2 --option3 value3 --option4 value4 --option5 value5
