---
type: Styleguide Rule
description: Complex regex patterns should be broken down into simpler components or replaced with more maintainable alternatives. A regex is considered complex when it has 3+ capture groups, uses lookaheads/lookbehinds, or exceeds 80 characters.
language: rust
category: simplicity
rule_id: AVOID-COMPLEX-REGEX
priority: warn
tags:
- simplicity
- readability
- maintainability
---
Complex regex patterns should be broken down into simpler components or replaced with more maintainable alternatives. A regex is considered complex when it has 3+ capture groups, uses lookaheads/lookbehinds, or exceeds 80 characters.

## Good

- Use verbose mode with comments for complex patterns
- Break patterns into named components
- Use parser combinators for complex formats

## Bad

- Single-line regex with multiple nested groups and lookaheads
