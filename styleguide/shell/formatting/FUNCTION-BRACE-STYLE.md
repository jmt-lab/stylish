---
type: Styleguide Rule
description: Place the opening brace on the same line as the function name.
language: shell
category: formatting
rule_id: FUNCTION-BRACE-STYLE
priority: warn
tags:
- formatting
- functions
---
Place the opening brace on the same line as the function name.

## Good

- my_function() {
  echo "Hello"
}


## Bad

- my_function()
{
  echo "Hello"
}

