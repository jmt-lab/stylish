---
type: Styleguide Rule
description: |-
  When a value might be absent (not an error, just not present),
  use Option<T> instead of Result.
language: rust
category: error_handling
rule_id: OPTION-FOR-ABSENCE
priority: error
tags:
- errors
- option
- absence
---
When a value might be absent (not an error, just not present),
use Option<T> instead of Result.

## Good

- fn find_entity(&self, id: EntityId) -> Option<&Entity>
- fn get_cached(&self, key: &Key) -> Option<&Value>

## Bad

- fn find_entity(&self, id: EntityId) -> Result<&Entity, Error> // Not an error to not find
