---
type: Styleguide Rule
description: All shell scripts must be validated with ShellCheck. It is irresponsible to not use static analysis.
language: shell
category: features
rule_id: USE-SHELLCHECK
priority: error
tags:
- static-analysis
- tooling
- quality
---
All shell scripts must be validated with ShellCheck. It is irresponsible to not use static analysis.

## Good

- # Run shellcheck on all scripts in CI/CD
- shellcheck -x script.sh

## Bad

- # No static analysis performed
