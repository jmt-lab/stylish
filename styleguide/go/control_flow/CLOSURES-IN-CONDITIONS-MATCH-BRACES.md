---
type: Styleguide Rule
description: |-
  When an if statement contains a closure or multi-line literal, keep the
  braces matched so that }); err != nil { sits at the if statement's
  indentation.
language: go
category: control_flow
rule_id: CLOSURES-IN-CONDITIONS-MATCH-BRACES
priority: info
tags:
- conditionals
- closures
- braces
- google-style
---
When an if statement contains a closure or multi-line literal, keep the
braces matched so that }); err != nil { sits at the if statement's
indentation.

## Good

- if err := db.RunInTransaction(func(tx *db.TX) error {
    return tx.Execute(userUpdate, x, y, z)
}); err != nil {
    return fmt.Errorf("user update failed: %s", err)
}

## Bad

- if err := db.RunInTransaction(func(tx *db.TX) error {
        return tx.Execute(userUpdate, x, y, z)
    }); err != nil {
    return err
}
