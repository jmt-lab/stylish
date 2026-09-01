---
type: Styleguide Rule
description: |-
  Different analyzers catch different issues. Use multiple tools
  for comprehensive coverage (compiler, linters, specialized analyzers).
language: language-agnostic
category: static_analysis
rule_id: MULTIPLE-ANALYZERS
priority: warn
tags:
- tools
- coverage
- redundancy
---
Different analyzers catch different issues. Use multiple tools
for comprehensive coverage (compiler, linters, specialized analyzers).

## Good

- # Using: GCC warnings, Clang analyzer, PVS-Studio

## Bad

- # Using: only basic compiler warnings
