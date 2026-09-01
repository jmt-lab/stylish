---
type: Styleguide Rule
description: |-
  Major subsystems should have their own directories. Directory structure
  should reflect architectural boundaries.
language: language-agnostic
category: organization
rule_id: SUBSYSTEM-DIRECTORIES
priority: warn
tags:
- directories
- architecture
- organization
---
Major subsystems should have their own directories. Directory structure
should reflect architectural boundaries.

## Good

- renderer/ - Graphics subsystem
- sound/ - Audio subsystem
- game/ - Game logic
- platform/ - OS abstraction

## Bad

- src/ - Everything in one folder
- lib/ - Mixed purposes
