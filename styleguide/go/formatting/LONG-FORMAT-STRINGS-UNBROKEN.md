---
type: Styleguide Rule
description: |-
  Do not split long format strings for line length. Break after the format
  string and group the remaining arguments semantically.
language: go
category: formatting
rule_id: LONG-FORMAT-STRINGS-UNBROKEN
priority: warn
tags:
- strings
- line-length
- logging
- google-style
---
Do not split long format strings for line length. Break after the format
string and group the remaining arguments semantically.

## Good

- log.Warningf("Database key (%q, %d, %q) incompatible in transaction started by (%q, %d, %q)",
    currentCustomer, currentOffset, currentKey,
    txCustomer, txOffset, txKey)

## Bad

- log.Warningf("Database key (%q, %d, %q) incompatible in"+
    " transaction started by (%q, %d, %q)",
    currentCustomer, currentOffset, currentKey, txCustomer,
    txOffset, txKey)
