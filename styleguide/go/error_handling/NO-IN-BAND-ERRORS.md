---
type: Styleguide Rule
description: |-
  Do not signal errors or missing values in-band with values like -1, nil, or
  "". Return an extra final value (ok bool or error) so callers cannot
  accidentally use an invalid result.
language: go
category: error_handling
rule_id: NO-IN-BAND-ERRORS
priority: warn
tags:
- errors
- multiple-returns
- google-style
---
Do not signal errors or missing values in-band with values like -1, nil, or
"". Return an extra final value (ok bool or error) so callers cannot
accidentally use an invalid result.

## Good

- // Lookup returns the value for key or ok=false if there is no mapping.
func Lookup(key string) (value string, ok bool)

value, ok := Lookup(key)
if !ok {
    return fmt.Errorf("no value for %q", key)
}

## Bad

- // Lookup returns the value for key or -1 if there is no mapping.
func Lookup(key string) int
- return Parse(Lookup(missingKey)) // misattributes the failure to Parse
