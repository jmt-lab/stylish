---
type: Styleguide Rule
description: |-
  Run bandit to catch common security issues. Check for hardcoded
  secrets, SQL injection, unsafe deserialization.
language: python
category: practices
rule_id: BANDIT-SECURITY
priority: warn
tags:
- bandit
- security
- scanning
---
Run bandit to catch common security issues. Check for hardcoded
secrets, SQL injection, unsafe deserialization.

## Good

- bandit -r src/ -ll

## Bad

- # No security scanning
