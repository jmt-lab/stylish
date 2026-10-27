---
type: Styleguide Rule
description: |-
  Use godoc's minimal formatting: blank comment lines between paragraphs,
  extra indentation for verbatim code, lists, and tables, and no other
  decoration. Preview the rendered docs during development and review.
language: go
category: comments
rule_id: GODOC-FORMATTING
priority: info
tags:
- documentation
- godoc
- formatting
- google-style
---
Use godoc's minimal formatting: blank comment lines between paragraphs,
extra indentation for verbatim code, lists, and tables, and no other
decoration. Preview the rendered docs during development and review.

## Good

- // LoadConfig reads a configuration out of the named file.
//
// LoadConfig treats the following keys in special ways:
//   "import" will make this configuration inherit from the named file.
//   "env" if present will be populated with the system environment.

## Bad

- // LoadConfig reads a configuration out of the named file.
// **Special keys**: "import" -> inherit, "env" -> environment
// ==============================================
