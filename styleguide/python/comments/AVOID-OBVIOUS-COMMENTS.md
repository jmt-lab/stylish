---
type: Styleguide Rule
description: Don't add comments that restate what Python code clearly expresses. Pythonic code is self-documenting.
language: python
category: comments
rule_id: AVOID-OBVIOUS-COMMENTS
priority: warn
tags:
- noise
- clarity
- antipattern
---
Don't add comments that restate what Python code clearly expresses. Pythonic code is self-documenting.

## Good

- count += 1  # No comment needed

## Bad

- count += 1  # Increment count
- return True  # Return True
