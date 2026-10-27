---
type: Styleguide Rule
description: |-
  Do not hide critical behavior in a single easily missed character (= vs :=,
  a buried !). Split the logic into named steps or call it out with a comment.
language: go
category: principles
rule_id: DONT-HIDE-CRITICAL-DETAILS
priority: info
tags:
- maintainability
- clarity
- google-style
---
Do not hide critical behavior in a single easily missed character (= vs :=,
a buried !). Split the logic into named steps or call it out with a comment.

## Good

- u, err := db.UserByID(userID)
if err != nil {
    return fmt.Errorf("invalid origin user: %s", err)
}
user = u
- leap4, leap100, leap400 := year%4 == 0, year%100 == 0, year%400 == 0
leap := leap4 && (!leap100 || leap400)

## Bad

- if user, err = db.UserByID(userID); err != nil { ... } // = vs := changes meaning
- leap := (year%4 == 0) && (!(year%100 == 0) || (year%400 == 0))
