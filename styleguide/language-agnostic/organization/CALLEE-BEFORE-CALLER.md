---
type: Styleguide Rule
description: |-
  Functions should be ordered so called functions appear before calling
  functions. This eliminates forward declarations and makes dependency
  flow obvious when reading top-to-bottom.
language: language-agnostic
category: organization
rule_id: CALLEE-BEFORE-CALLER
priority: info
tags:
- functions
- ordering
- readability
---
Functions should be ordered so called functions appear before calling
functions. This eliminates forward declarations and makes dependency
flow obvious when reading top-to-bottom.

## Good

- // Helper appears first
void Helper() {}
// Caller appears after
void Main() { Helper(); }

## Bad

- // Forward declaration needed
void Main();
void Helper() {}
void Main() { Helper(); }
