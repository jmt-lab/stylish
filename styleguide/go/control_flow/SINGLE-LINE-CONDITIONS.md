---
type: Styleguide Rule
description: |-
  Do not line-break if conditions. Extract boolean operands or repeated
  subexpressions into named locals (when short-circuiting is not needed), or
  let the line be long.
language: go
category: control_flow
rule_id: SINGLE-LINE-CONDITIONS
priority: warn
tags:
- conditionals
- indentation
- google-style
---
Do not line-break if conditions. Extract boolean operands or repeated
subexpressions into named locals (when short-circuiting is not needed), or
let the line be long.

## Good

- inTransaction := db.CurrentStatusIs(db.InTransaction)
keysMatch := db.ValuesEqual(db.TransactionKey(), row.Key())
if inTransaction && keysMatch {
    return errTxKeyMismatch
}
- uid := user.GetUniqueUserID()
if db.UserIsAdmin(uid) || db.UserHasPermission(uid, perms.CreateGroup) {}

## Bad

- if db.CurrentStatusIs(db.InTransaction) &&
    db.ValuesEqual(db.TransactionKey(), row.Key()) {
    return errTxKeyMismatch
}
