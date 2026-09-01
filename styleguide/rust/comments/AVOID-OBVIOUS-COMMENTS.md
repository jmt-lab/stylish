---
type: Styleguide Rule
description: |-
  Don't add comments that merely restate what the code clearly does.
  This adds noise without value.
language: rust
category: comments
rule_id: AVOID-OBVIOUS-COMMENTS
priority: warn
tags:
- comments
- noise
- carmack
---
Don't add comments that merely restate what the code clearly does.
This adds noise without value.

## Good

- count += 1; // No comment needed

## Bad

- count += 1; // Increment count
- return true; // Return true
