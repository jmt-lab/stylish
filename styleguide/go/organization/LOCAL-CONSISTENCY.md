---
type: Styleguide Rule
description: |-
  Where the style guide is silent, follow the established style of nearby code
  (same file or package). Local consistency never justifies spreading or
  worsening a real style-guide violation.
language: go
category: organization
rule_id: LOCAL-CONSISTENCY
priority: info
tags:
- consistency
- style
- google-style
---
Where the style guide is silent, follow the established style of nearby code
(same file or package). Local consistency never justifies spreading or
worsening a real style-guide violation.

## Good

- // package already formats errors with %v; new code follows suit
return fmt.Errorf("load config: %v", err)

## Bad

- // mixing %s and %v for errors in the same file without reason
return fmt.Errorf("load: %s", err)
return fmt.Errorf("save: %v", err)
