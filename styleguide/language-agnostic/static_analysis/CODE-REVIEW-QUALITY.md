---
type: Styleguide Rule
description: |-
  Use static analysis and automated tools for style and common bugs.
  Reserve human code review for algorithmic correctness and design.
language: language-agnostic
category: static_analysis
rule_id: CODE-REVIEW-QUALITY
priority: info
tags:
- code-review
- automation
- efficiency
---
Use static analysis and automated tools for style and common bugs.
Reserve human code review for algorithmic correctness and design.

## Good

- # Reviewers focus on: algorithm, edge cases, design
# Automation checks: style, common bugs

## Bad

- # Reviewers argue about: formatting, naming
# No automation
