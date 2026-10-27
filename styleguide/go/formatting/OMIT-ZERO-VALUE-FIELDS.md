---
type: Styleguide Rule
description: |-
  Omit zero-value fields from struct literals when clarity is not lost, so the
  fields that matter stand out. In test tables, include a zero value only when
  it is meaningful to the case.
language: go
category: formatting
rule_id: OMIT-ZERO-VALUE-FIELDS
priority: info
tags:
- literals
- zero-values
- google-style
---
Omit zero-value fields from struct literals when clarity is not lost, so the
fields that matter stand out. In test tables, include a zero value only when
it is meaningful to the case.

## Good

- ldb := leveldb.Open("/my/table", &db.Options{
    BlockSize:       1 << 16,
    ErrorIfDBExists: true,
})

## Bad

- ldb := leveldb.Open("/my/table", &db.Options{
    BlockSize:            1 << 16,
    ErrorIfDBExists:      true,
    BlockRestartInterval: 0,
    Comparer:             nil,
    Compression:          nil,
    VerifyChecksums:      false,
})
