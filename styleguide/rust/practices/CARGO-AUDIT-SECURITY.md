---
type: Styleguide Rule
description: |-
  Install cargo-audit and run security audits regularly. Update vulnerable
  dependencies when advisories are found. Document accepted risks for
  unavoidable vulnerabilities. Set up automated audit checks in CI/CD.
language: rust
category: practices
rule_id: CARGO-AUDIT-SECURITY
priority: error
tags:
- development
- security
- dependencies
---
Install cargo-audit and run security audits regularly. Update vulnerable
dependencies when advisories are found. Document accepted risks for
unavoidable vulnerabilities. Set up automated audit checks in CI/CD.

## Good

- cargo install cargo-audit
- cargo audit

## Bad

- # Never check for known security vulnerabilities
