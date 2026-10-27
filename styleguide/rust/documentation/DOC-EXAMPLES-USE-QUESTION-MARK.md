---
type: Styleguide Rule
description: |-
  Doc examples use ? (with the fn main scaffolding hidden behind # lines),
  never unwrap() or expect(), because users copy them verbatim.
language: rust
category: documentation
rule_id: DOC-EXAMPLES-USE-QUESTION-MARK
priority: warn
tags:
- documentation
- examples
- error-handling
- beautiful-rust
---
Doc examples use ? (with the fn main scaffolding hidden behind # lines),
never unwrap() or expect(), because users copy them verbatim.

## Good

- /// ```
/// # use mycrate::Version;
/// # fn main() -> Result<(), Box<dyn std::error::Error>> {
/// let version = Version::parse("1.2.3")?;
/// assert_eq!(version.major(), 1);
/// # Ok(())
/// # }
/// ```

## Bad

- /// ```
/// let version = Version::parse("1.2.3").unwrap();
/// ```
