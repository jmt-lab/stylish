---
type: Styleguide Rule
description: |-
  Exported functions should return errors as the error interface, not concrete
  error types. A nil concrete pointer wrapped in an interface is non-nil and
  causes subtle bugs.
language: go
category: error_handling
rule_id: RETURN-ERROR-INTERFACE
priority: warn
tags:
- errors
- interfaces
- nil
- google-style
---
Exported functions should return errors as the error interface, not concrete
error types. A nil concrete pointer wrapped in an interface is non-nil and
causes subtle bugs.

## Good

- func Chdir(dir string) error // documented to return *PathError

## Bad

- func Chdir(dir string) *os.PathError
- var perr *os.PathError
return perr // as error: non-nil interface holding a nil pointer
