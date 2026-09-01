---
type: Styleguide Rule
description: Separate additional context from the summary line with an empty line.
language: rust
category: documentation
rule_id: SUMMARY-SEPARATION
priority: error
tags:
- documentation
- formatting
---
Separate additional context from the summary line with an empty line.

## Good

- /// Processes the input buffer.
///
/// This function applies transformations...

## Bad

- /// Processes the input buffer.
/// This function applies transformations...
