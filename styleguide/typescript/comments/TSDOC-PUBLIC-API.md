---
type: Styleguide Rule
description: |-
  All exported functions, classes, and interfaces must have TSDoc comments
  (/** */). Private implementation details don't require TSDoc but may have
  explanatory comments when needed.
language: typescript
category: comments
rule_id: TSDOC-PUBLIC-API
priority: error
tags:
- documentation
- tsdoc
- public-api
---
All exported functions, classes, and interfaces must have TSDoc comments
(/** */). Private implementation details don't require TSDoc but may have
explanatory comments when needed.

## Good

- /**
 * Formats numbers with thousand separators.
 * Uses locale-aware formatting to handle international conventions.
 */
export function formatNumber(value: number): string


## Bad

- export function formatNumber(value: number): string // formats numbers
- // Public function export function formatNumber(value: number): string
