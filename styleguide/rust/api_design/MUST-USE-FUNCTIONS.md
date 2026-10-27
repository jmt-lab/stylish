---
type: Styleguide Rule
description: |-
  Mark functions #[must_use] when ignoring the return value is a mistake:
  pure functions with no side effects (e.g. HashMap::get) and functions whose
  return value reports an error or other critical information. Skip it when
  the return type is already #[must_use] (e.g. Result).
language: rust
category: api_design
rule_id: MUST-USE-FUNCTIONS
priority: warn
tags:
- api-design
- attributes
- must-use
- google-style
---
Mark functions #[must_use] when ignoring the return value is a mistake:
pure functions with no side effects (e.g. HashMap::get) and functions whose
return value reports an error or other critical information. Skip it when
the return type is already #[must_use] (e.g. Result).

## Good

- #[must_use]
pub fn with_timeout(self, timeout: Duration) -> Self { ... }
- #[must_use]
pub fn checked_sub(self, rhs: Self) -> Option<Self> { ... }

## Bad

- pub fn with_timeout(self, timeout: Duration) -> Self { ... }

client.with_timeout(Duration::from_secs(5)); // silently discarded
- #[must_use] // redundant: Result is already #[must_use]
pub fn save(&self) -> Result<(), SaveError> { ... }
