---
type: Styleguide Rule
description: |-
  It is irresponsible to not use static analysis. Run analyzers
  continuously as part of CI — block merges that introduce new warnings
  or issues. Enable maximum warning levels (-Wall -Wextra or equivalent)
  and treat every warning as a potential bug. Maintain a zero-warnings
  policy: fix new warnings immediately, don't let them accumulate, as
  they hide real problems.
language: language-agnostic
category: static_analysis
rule_id: STATIC-ANALYSIS-MANDATORY
priority: error
tags:
- static-analysis
- quality
- mandatory
- ci
- automation
- enforcement
- compiler
- warnings
- strictness
- discipline
- hygiene
---
It is irresponsible to not use static analysis. Run analyzers
continuously as part of CI — block merges that introduce new warnings
or issues. Enable maximum warning levels (-Wall -Wextra or equivalent)
and treat every warning as a potential bug. Maintain a zero-warnings
policy: fix new warnings immediately, don't let them accumulate, as
they hide real problems.

## Good

- # CI pipeline runs static analysis
# Build fails on new warnings
- gcc -Wall -Wextra -Werror
- # 0 warnings in build output
- # PR blocked on new analyzer issues

## Bad

- # No static analysis
# Warnings ignored
- gcc # Default warnings only
- # 2,453 warnings (what's 1 more?)
- # Manual analysis only
# Easy to skip
