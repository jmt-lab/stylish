---
type: Styleguide Rule
description: |-
  Start with @typescript-eslint/recommended ruleset. Add stricter
  rules as needed. Don't disable rules without strong justification.
language: typescript
category: practices
rule_id: RECOMMENDED-RULES
priority: error
tags:
- eslint
- configuration
- defaults
---
Start with @typescript-eslint/recommended ruleset. Add stricter
rules as needed. Don't disable rules without strong justification.

## Good

- extends: ["@typescript-eslint/recommended"]

## Bad

- // Custom minimal ruleset, missing common checks
