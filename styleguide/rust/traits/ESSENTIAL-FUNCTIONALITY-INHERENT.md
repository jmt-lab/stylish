---
type: Styleguide Rule
description: |-
  Put a type's essential functionality in inherent methods and have trait
  impls forward to them, so callers don't need to import a trait to use the
  core API.
language: rust
category: traits
rule_id: ESSENTIAL-FUNCTIONALITY-INHERENT
priority: info
tags:
- traits
- discoverability
- api-design
- beautiful-rust
---
Put a type's essential functionality in inherent methods and have trait
impls forward to them, so callers don't need to import a trait to use the
core API.

## Good

- impl Matrix { pub fn transpose(&self) -> Self { ... } }
impl Transpose for Matrix { fn transpose(&self) -> Self { Matrix::transpose(self) } }

## Bad

- impl Transpose for Matrix { fn transpose(&self) -> Self { ... } }
// matrix.transpose() fails to compile until the caller imports Transpose
