---
type: Styleguide Rule
description: Never include explicit documentation about when functions return errors. Let error types in the function signature communicate failure modes.
language: rust
category: documentation
rule_id: NO-ERROR-DOCS
priority: info
tags:
- documentation
- errors
- redundancy
---
Never include explicit documentation about when functions return errors. Let error types in the function signature communicate failure modes.

## Bad

- /// # Errors
/// Returns `IoError` if file cannot be read
