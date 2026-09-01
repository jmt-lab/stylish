---
type: Styleguide Rule
description: |-
  Complex or non-obvious functions should include usage examples in
  doc comments using code blocks.
language: rust
category: documentation
rule_id: DOC-EXAMPLES
priority: warn
tags:
- documentation
- examples
---
Complex or non-obvious functions should include usage examples in
doc comments using code blocks.

## Good

- /// Parses configuration from TOML.
///
/// # Example
/// ```
/// let config = Config::from_toml(data)?;
/// assert_eq!(config.width, 1920);
/// ```

## Bad

- /// Parses configuration. // No example of how to use
