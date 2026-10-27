---
type: Styleguide Rule
description: |-
  Name packages after what they provide. Avoid uninformative names like util,
  helper, common, model or testhelper; they read poorly at call sites and
  cause import conflicts.
language: go
category: naming
rule_id: NO-UTIL-PACKAGE-NAMES
priority: warn
tags:
- packages
- readability
- google-style
---
Name packages after what they provide. Avoid uninformative names like util,
helper, common, model or testhelper; they read poorly at call sites and
cause import conflicts.

## Good

- db := spannertest.NewDatabaseFromFile(path)
- b := elliptic.Marshal(curve, x, y)

## Bad

- db := test.NewDatabaseFromFile(path) // what kind of test?
- b := helper.Marshal(curve, x, y) // helper says nothing
- _, err := f.Seek(0, common.SeekStart)
