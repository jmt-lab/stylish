---
type: Styleguide Rule
description: |-
  Comments should be on their own line rather than following code
  on the same line. Exceptions for very short clarifications.
language: rust
category: comments
rule_id: STANDALONE-COMMENTS
priority: info
tags:
- comments
- placement
- official
---
Comments should be on their own line rather than following code
on the same line. Exceptions for very short clarifications.

## Good

- // Process each entity
for entity in entities {

## Bad

- for entity in entities { // Process each entity
