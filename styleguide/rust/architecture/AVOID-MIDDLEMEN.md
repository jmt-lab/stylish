---
type: Styleguide Rule
description: Remove pure delegation methods that add no value. Eliminate wrapper types that only forward calls without transformation or validation.
language: rust
category: architecture
rule_id: AVOID-MIDDLEMEN
priority: warn
tags:
- architecture
- simplicity
- abstraction
---
Remove pure delegation methods that add no value. Eliminate wrapper types that only forward calls without transformation or validation.

## Bad

- impl Wrapper { fn do_thing(&self) { self.inner.do_thing() } }
