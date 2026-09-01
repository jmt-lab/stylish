---
type: Styleguide Rule
description: |-
  Don't add comments that merely restate what the code clearly does.
  TypeScript's type system makes much code self-documenting.
language: typescript
category: comments
rule_id: AVOID-OBVIOUS-COMMENTS
priority: warn
tags:
- noise
- clarity
- antipattern
---
Don't add comments that merely restate what the code clearly does.
TypeScript's type system makes much code self-documenting.

## Good

- count++; // No comment needed

## Bad

- count++; // Increment count
- return true; // Return true
- const user: User = getUser(); // Get user
