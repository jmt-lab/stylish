---
type: Styleguide Rule
description: |-
  Run npm audit or yarn audit regularly. Fix security vulnerabilities.
  Automate in CI to catch new issues.
language: typescript
category: practices
rule_id: DEPENDENCY-AUDIT
priority: warn
tags:
- security
- dependencies
- npm
---
Run npm audit or yarn audit regularly. Fix security vulnerabilities.
Automate in CI to catch new issues.

## Good

- // CI runs: npm audit --audit-level=moderate

## Bad

- // Dependencies never audited
