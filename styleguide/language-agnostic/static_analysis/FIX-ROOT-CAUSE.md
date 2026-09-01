---
type: Styleguide Rule
description: |-
  When static analysis finds a bug, investigate why the pattern
  exists. Often reveals systemic issues that need broader fixes.
language: language-agnostic
category: static_analysis
rule_id: FIX-ROOT-CAUSE
priority: warn
tags:
- root-cause
- systemic
- thoroughness
---
When static analysis finds a bug, investigate why the pattern
exists. Often reveals systemic issues that need broader fixes.

## Good

- # Bug: missing NULL check
# Fix: add NULL check + audit all similar code

## Bad

- # Bug: missing NULL check
# Fix: add NULL check (done, move on)
