---
type: Styleguide Rule
description: |-
  Don't add comments that merely restate what the code clearly does.
  This adds noise without value.
language: language-agnostic
category: comments
rule_id: AVOID-OBVIOUS-COMMENTS
priority: warn
tags:
- noise
- clarity
- antipattern
---
Don't add comments that merely restate what the code clearly does.
This adds noise without value.

## Good

- count++;

## Bad

- count++; // Increment count
- return true; // Return true
