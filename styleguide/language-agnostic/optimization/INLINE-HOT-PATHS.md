---
type: Styleguide Rule
description: |-
  Use inline for small, frequently-called functions in performance
  critical code. Don't over-inline; measure the impact.
language: language-agnostic
category: optimization
rule_id: INLINE-HOT-PATHS
priority: warn
tags:
- inlining
- hot-path
- micro-optimization
---
Use inline for small, frequently-called functions in performance
critical code. Don't over-inline; measure the impact.

## Good

- inline float Vec3::Length() const // Called millions of times

## Bad

- inline void LoadLevel() // Large, called once
