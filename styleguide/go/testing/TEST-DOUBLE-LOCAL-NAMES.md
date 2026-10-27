---
type: Styleguide Rule
description: |-
  Name test-local variables holding doubles so they stand out from production
  values, for example spyCC instead of cc.
language: go
category: testing
rule_id: TEST-DOUBLE-LOCAL-NAMES
priority: hint
tags:
- testing
- test-doubles
- naming
- google-style
---
Name test-local variables holding doubles so they stand out from production
values, for example spyCC instead of cc.

## Good

- var spyCC creditcardtest.Spy
proc := &Processor{CC: spyCC}

## Bad

- var cc creditcardtest.Spy // reads like a real card client
