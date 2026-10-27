---
type: Styleguide Rule
description: |-
  Use the non-formatting log call (log.Info(v)) when there is nothing to
  format, rather than log.Infof("%v", v).
language: go
category: practices
rule_id: LOG-WITHOUT-FORMAT
priority: hint
tags:
- logging
- google-style
---
Use the non-formatting log call (log.Info(v)) when there is nothing to
format, rather than log.Infof("%v", v).

## Good

- log.Info(msg)
- log.Infof("Processed %d items", n)

## Bad

- log.Infof("%v", msg)
