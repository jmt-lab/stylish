---
type: Styleguide Rule
description: |-
  Signal failure by returning error as the last result, nil on success. When
  an error is returned, treat the other results as unspecified unless
  documented. Functions that take a context.Context should usually return an
  error.
language: go
category: error_handling
rule_id: ERROR-LAST-RESULT
priority: warn
tags:
- errors
- signatures
- google-style
---
Signal failure by returning error as the last result, nil on success. When
an error is returned, treat the other results as unspecified unless
documented. Functions that take a context.Context should usually return an
error.

## Good

- func Lookup(id string) (*Result, error) {
    if err != nil {
        return nil, err
    }
    return res, nil
}

## Bad

- func Lookup(id string) (error, *Result) // error must be last
- res, err := Lookup(id)
use(res) // relying on res before checking err
