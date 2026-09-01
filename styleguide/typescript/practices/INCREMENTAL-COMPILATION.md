---
type: Styleguide Rule
description: |-
  Use incremental: true and composite for faster rebuilds. Especially
  important in large codebases and CI.
language: typescript
category: practices
rule_id: INCREMENTAL-COMPILATION
priority: info
tags:
- performance
- compilation
- speed
---
Use incremental: true and composite for faster rebuilds. Especially
important in large codebases and CI.

## Good

- {"compilerOptions": {"incremental": true}}

## Bad

- // Full recompilation every time
