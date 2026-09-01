---
type: Styleguide Rule
description: |-
  Keep try blocks as small as possible. Only wrap code that can actually
  raise the exception you're catching.
language: python
category: error_handling
rule_id: NARROW-EXCEPT-SCOPE
priority: warn
tags:
- exceptions
- clarity
- debugging
---
Keep try blocks as small as possible. Only wrap code that can actually
raise the exception you're catching.

## Good

- data = prepare()
try:
    result = risky_operation(data)
except ValueError:
    handle_error()

## Bad

- try:
    data = prepare()
    result = risky_operation(data)
    more_code()
except ValueError:
    pass  # Which line failed?
