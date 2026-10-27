---
type: Styleguide Rule
description: |-
  Do not wrap a line so its continuation aligns with the indented block that
  follows. If a break is unavoidable, separate the wrapped line from the
  block.
language: go
category: formatting
rule_id: AVOID-INDENTATION-CONFUSION
priority: warn
tags:
- indentation
- readability
- google-style
---
Do not wrap a line so its continuation aligns with the indented block that
follows. If a break is unavoidable, separate the wrapped line from the
block.

## Good

- cond12 := longCondition1 && longCondition2
cond34 := longCondition3 && longCondition4
if cond12 && cond34 {
    log.Info("all conditions met")
}

## Bad

- if longCondition1 && longCondition2 &&
    longCondition3 && longCondition4 {
    log.Info("all conditions met") // same indent as the condition
}
