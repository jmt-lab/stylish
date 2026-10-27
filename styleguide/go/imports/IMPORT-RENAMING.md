---
type: Styleguide Rule
description: |-
  Do not rename imports without a reason. Rename to resolve a collision
  (preferring to rename the most local import), to remove underscores from
  generated packages, or, sparingly, when a name is uninformative (v1, util).
  Aliases must follow package naming rules.
language: go
category: imports
rule_id: IMPORT-RENAMING
priority: warn
tags:
- imports
- packages
- google-style
---
Do not rename imports without a reason. Rename to resolve a collision
(preferring to rename the most local import), to remove underscores from
generated packages, or, sparingly, when a name is uninformative (v1, util).
Aliases must follow package naming rules.

## Good

- import (
    core "github.com/kubernetes/api/core/v1"
    meta "github.com/kubernetes/apimachinery/pkg/apis/meta/v1beta1"
)

## Bad

- import (
    myFmt "fmt" // pointless rename, mixed case
    str "strings"
)
