---
type: Styleguide Rule
description: Never document function parameters or return values in docstrings. Rely on well-named parameters and clear type signatures.
language: rust
category: documentation
rule_id: NO-PARAM-DOCS
priority: info
tags:
- documentation
- redundancy
---
Never document function parameters or return values in docstrings. Rely on well-named parameters and clear type signatures.

## Bad

- /// # Arguments
/// * `x` - The x coordinate
/// * `y` - The y coordinate
- /// # Returns
/// The computed distance
