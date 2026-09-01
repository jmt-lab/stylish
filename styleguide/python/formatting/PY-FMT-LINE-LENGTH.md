---
type: Styleguide Rule
description: Keep lines to 88-100 characters. Black defaults to 88; 100 is acceptable for readability.
language: python
category: formatting
rule_id: PY-FMT-LINE-LENGTH
priority: warn
tags:
- formatting
- readability
- line-length
---
Keep lines to 88-100 characters. Black defaults to 88; 100 is acceptable for readability.

## Good

- result = some_function(arg1, arg2, arg3)
- result = some_function(
    arg1, arg2, arg3, arg4
)


## Bad

- result = some_function(arg1, arg2, arg3, arg4, arg5, arg6, arg7, arg8, arg9, arg10, arg11, arg12)
