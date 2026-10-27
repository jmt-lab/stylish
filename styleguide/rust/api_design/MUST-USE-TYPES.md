---
type: Styleguide Rule
description: |-
  Mark types #[must_use] when every function returning them would otherwise
  need #[must_use]: error/status types and lazily evaluated computations
  (futures, builders, guards) whose value must be used to have an effect.
language: rust
category: api_design
rule_id: MUST-USE-TYPES
priority: warn
tags:
- api-design
- attributes
- must-use
- types
- google-style
---
Mark types #[must_use] when every function returning them would otherwise
need #[must_use]: error/status types and lazily evaluated computations
(futures, builders, guards) whose value must be used to have an effect.

## Good

- #[must_use = "a Query does nothing until executed"]
pub struct Query { ... }
- #[must_use]
pub struct ValidationReport { pub errors: Vec<Issue> }

## Bad

- pub struct Query { ... }

db.select("users"); // builds a query and drops it without running
