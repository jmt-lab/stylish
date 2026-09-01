---
type: Styleguide Rule
description: |-
  If const must be cast away (const_cast or similar), document why this
  is necessary and safe. This should be rare.
language: language-agnostic
category: const_usage
rule_id: DOCUMENT-CONST-CAST
priority: error
tags:
- const-cast
- safety
- documentation
---
If const must be cast away (const_cast or similar), document why this
is necessary and safe. This should be rare.

## Good

- // SAFE: Legacy API requires non-const but doesn't modify
LegacyFunc(const_cast<char*>(str));

## Bad

- LegacyFunc(const_cast<char*>(str)); // No explanation
