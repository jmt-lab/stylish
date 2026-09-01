---
type: Styleguide Rule
description: |-
  When code has platform-specific behavior or workarounds, document
  why and what platforms are affected.
language: language-agnostic
category: comments
rule_id: PLATFORM-SPECIFIC-NOTES
priority: warn
tags:
- platform
- portability
- documentation
---
When code has platform-specific behavior or workarounds, document
why and what platforms are affected.

## Good

- // Windows requires backslashes in paths
path = path.replace('/', '\\');
- // Linux-specific: case-sensitive filesystem

## Bad

- // Special case
if (PLATFORM_WINDOWS)
