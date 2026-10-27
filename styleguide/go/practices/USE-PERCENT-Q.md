---
type: Styleguide Rule
description: |-
  Use %q to quote strings in output meant for humans, especially when a value
  could be empty or contain control characters. Do not hand-quote with "%s" or
  '%s'.
language: go
category: practices
rule_id: USE-PERCENT-Q
priority: info
tags:
- fmt
- strings
- output
- google-style
---
Use %q to quote strings in output meant for humans, especially when a value
could be empty or contain control characters. Do not hand-quote with "%s" or
'%s'.

## Good

- fmt.Printf("value %q looks like English text", someText)

## Bad

- fmt.Printf("value \"%s\" looks like English text", someText)
- fmt.Printf("value '%s' looks like English text", someText)
