---
type: Styleguide Rule
description: |-
  When annotating an error, add context only the current function has; do not
  repeat what the underlying error already says. Do not add annotations like
  "failed" that just restate that an error occurred.
language: go
category: error_handling
rule_id: ADD-NON-REDUNDANT-CONTEXT
priority: info
tags:
- errors
- wrapping
- messages
- google-style
---
When annotating an error, add context only the current function has; do not
repeat what the underlying error already says. Do not add annotations like
"failed" that just restate that an error occurred.

## Good

- if err := os.Open("settings.txt"); err != nil {
    return fmt.Errorf("launch codes unavailable: %v", err)
}
// launch codes unavailable: open settings.txt: no such file or directory

## Bad

- return fmt.Errorf("could not open settings.txt: %v", err)
// could not open settings.txt: open settings.txt: no such file or directory
- return fmt.Errorf("failed: %v", err) // just return err
