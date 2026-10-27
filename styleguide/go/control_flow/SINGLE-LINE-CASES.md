---
type: Styleguide Rule
description: |-
  Keep switch and case clauses on one line. If a case list is excessively
  long, put case alone on its line and indent every value on its own line.
language: go
category: control_flow
rule_id: SINGLE-LINE-CASES
priority: info
tags:
- switch
- indentation
- google-style
---
Keep switch and case clauses on one line. If a case list is excessively
long, put case alone on its line and indent every value on its own line.

## Good

- switch status {
case db.TransactionStarting, db.TransactionActive, db.TransactionWaiting:
    // ...
}
- switch db.TransactionStatus() {
case
    db.TransactionStarting,
    db.TransactionActive,
    db.TransactionWaiting:
    // ...
}

## Bad

- switch status {
case db.TransactionStarting,
    db.TransactionActive:
    // ...
}
