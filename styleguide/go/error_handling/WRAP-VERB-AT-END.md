---
type: Styleguide Rule
description: |-
  Put %w at the end of the message ("context: %w") so printed text runs newest
  to oldest like the chain. The exception is sentinel categories, which go
  first ("%w: details") so the category is prominent.
language: go
category: error_handling
rule_id: WRAP-VERB-AT-END
priority: info
tags:
- errors
- wrapping
- messages
- google-style
---
Put %w at the end of the message ("context: %w") so printed text runs newest
to oldest like the chain. The exception is sentinel categories, which go
first ("%w: details") so the category is prominent.

## Good

- err3 := fmt.Errorf("err3: %w", err2) // prints err3: err2: err1
- return fmt.Errorf("%w: invalid character in header: %v", ErrParseInvalidHeader, err)

## Bad

- err3 := fmt.Errorf("%w: err3", err2) // prints err1: err2: err3
- err3 := fmt.Errorf("err3-1 %w err3-2", err2) // jumbled order
- return fmt.Errorf("invalid character in header: %v: %w", err, ErrParseInvalidHeader) // category buried
