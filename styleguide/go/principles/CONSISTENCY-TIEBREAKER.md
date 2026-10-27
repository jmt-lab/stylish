---
type: Styleguide Rule
description: |-
  When other principles do not decide, choose the option consistent with
  similar code in the file, package, and wider codebase. Do not solve the same
  problem several ways or give one concept several names within a package.
language: go
category: principles
rule_id: CONSISTENCY-TIEBREAKER
priority: info
tags:
- consistency
- google-style
---
When other principles do not decide, choose the option consistent with
similar code in the file, package, and wider codebase. Do not solve the same
problem several ways or give one concept several names within a package.

## Good

- // all handlers in the package use the same request-validation helper
if err := validate(req); err != nil { return nil, err }

## Bad

- // handler A validates inline, handler B via helper, handler C not at all
