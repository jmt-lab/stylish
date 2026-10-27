---
type: Styleguide Rule
description: |-
  Guard expensive arguments to verbose logs with an explicit level check so
  they are not computed when that verbosity is off.
language: go
category: error_handling
rule_id: CHEAP-VERBOSE-LOGGING
priority: hint
tags:
- logging
- performance
- google-style
---
Guard expensive arguments to verbose logs with an explicit level check so
they are not computed when that verbosity is off.

## Good

- if log.V(2) {
    log.Infof("Handling %v", sql.Explain())
}

## Bad

- log.V(2).Infof("Handling %v", sql.Explain()) // Explain runs even when disabled
