---
type: Styleguide Rule
description: |-
  Enable address sanitizer, undefined behavior sanitizer, etc. in
  test builds. These catch bugs static analysis misses.
language: language-agnostic
category: static_analysis
rule_id: SANITIZERS-IN-TESTING
priority: warn
tags:
- sanitizers
- runtime
- testing
---
Enable address sanitizer, undefined behavior sanitizer, etc. in
test builds. These catch bugs static analysis misses.

## Good

- # Test build with ASAN, UBSAN, TSAN

## Bad

- # Plain test builds only
